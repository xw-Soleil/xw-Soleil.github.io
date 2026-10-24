# XZZD_Aquire_Score

> 这个记得是jiepeng哥一开始写了个只能查看作业分数的脚本，后来无意间发现了一个更好的包，后面便结合着gpt改良了一下；

## Introduction

这个记得是jiepeng哥一开始写了个只能查看作业分数的脚本，后来无意间发现了一个更好的包，后面便结合着gpt改良了一下；

能够将作业和考试的分数罗列在右下角建出来的面板之中

## Usage

将其放入油猴插件中启用即可

## Codes

```javascript
// ==UserScript==
// @name         XZZD_Score_findv1.1
// @namespace    http://tampermonkey.net/
// @version      1.1
// @description  Display homework scores on the page for various courses
// @author       Soleil
// @match        *://courses.zju.edu.cn/course/*/*
// @grant        none
// ==/UserScript==


(function() {
    'use strict';

    const courseUrlMatch = window.location.pathname.match(/\/course\/(\d+)\//);
    if (!courseUrlMatch) {
        console.error('Unable to find course ID in the URL.');
        return;
    }
    const courseId = courseUrlMatch[1];

    const scoreContainer = document.createElement('div');
    scoreContainer.id = 'score-container';
    scoreContainer.style.position = 'fixed';
    scoreContainer.style.bottom = '0';
    scoreContainer.style.right = '0';
    scoreContainer.style.zIndex = '1000';
    scoreContainer.style.backgroundColor = 'white';
    scoreContainer.style.border = '1px solid black';
    scoreContainer.style.maxHeight = '300px';
    scoreContainer.style.overflowY = 'auto';
    scoreContainer.style.padding = '10px';
    scoreContainer.style.width = '350px';
    document.body.appendChild(scoreContainer);

    let data_first;
    let data_second;

    const apiUrl = `https://courses.zju.edu.cn/api/course/${courseId}/activity-reads-for-user`;
    fetch(apiUrl)
        .then(response => response.json())
        .then(data => {
            console.log('Data from main API:', data); // Log to inspect the data structure
            const data_api = data;

            const apiUrl1 = `https://courses.zju.edu.cn/api/course/${courseId}/homework-scores?fields=id,title`;
            const apiUrl2 = `https://courses.zju.edu.cn/api/courses/${courseId}/exams`;

            return Promise.all([fetch(apiUrl1), fetch(apiUrl2), data_api]);  // 并行请求
        })
        .then(async ([response1, response2, data_api]) => {
            data_first = await response1.json(); // 第一个 API 的数据
            data_second = await response2.json(); // 第二个 API 的数据

            console.log('Data from API1:', data_first);
            console.log('Data from API2:', data_second);

            if (!data_first || !data_first.homework_activities) {
                console.error('Homework activities data is missing.');
                return;
            }

            if (!data_second || !data_second.exams) {
                console.error('Exams data is missing.');
                return;
            }

            const data_final = merge(data_second.exams, data_first.homework_activities, data_api.activity_reads);
            displayScores(data_final);
        })
        .catch(error => console.error('Error fetching the data:', error));

    function merge(examsActivities, homeworkActivities, activityReads) {
        const homeworkMap = new Map();
        const examsMap = new Map();

        homeworkActivities.forEach(activity => {
            homeworkMap.set(activity.id, activity.title);
        });

        examsActivities.forEach(exam => {
            examsMap.set(exam.id, exam.title);
        });

        const updatedActivityReads = activityReads.map(activityRead => {
            let title = 'Unknown Title';
            if (homeworkMap.has(activityRead.activity_id)) {
                title = homeworkMap.get(activityRead.activity_id);
            } else if (examsMap.has(activityRead.activity_id)) {
                title = examsMap.get(activityRead.activity_id);
            }

            return {
                ...activityRead,
                title
            };
        });

        console.log('Updated activity reads:', updatedActivityReads);
        return updatedActivityReads;
    }

    function displayScores(activityReads) {
        if (activityReads.length === 0) {
            scoreContainer.innerHTML = `<strong>No homework data available for course ${courseId}.</strong>`;
            return;
        }

        activityReads.forEach(activity => {
            const entry = document.createElement('div');
            entry.style.borderBottom = '1px solid #ddd';
            entry.style.marginBottom = '5px';
            entry.style.paddingBottom = '5px';

            if (activity.activity_type === "learning_activity") {
                if (activity.title != 'Unknown Title') {
                    entry.innerHTML = `<strong>Title:</strong> ${activity.title}<br>
                                       <strong>Score:</strong> ${activity.data.score}`;
                } else {
                    entry.innerHTML = `<strong>其他学习活动</strong>`;

                    const toggleButton = document.createElement('button');
                    toggleButton.innerText = '显示详情';
                    toggleButton.style.display = 'block';
                    toggleButton.style.marginTop = '5px';

                    const detailsContainer = document.createElement('div');
                    detailsContainer.style.display = 'none';
                    detailsContainer.style.marginTop = '5px';

                    for (const key in activity) {
                        if (activity.hasOwnProperty(key)) {
                            const detailEntry = document.createElement('div');
                            detailEntry.innerHTML = `<strong>${key}:</strong> ${activity[key]}`;
                            detailsContainer.appendChild(detailEntry);
                        }
                    }

                    toggleButton.addEventListener('click', () => {
                        if (detailsContainer.style.display === 'none') {
                            detailsContainer.style.display = 'block';
                            toggleButton.innerText = '隐藏详情';
                        } else {
                            detailsContainer.style.display = 'none';
                            toggleButton.innerText = '显示详情';
                        }
                    });

                    entry.appendChild(toggleButton);
                    entry.appendChild(detailsContainer);
                }
            } else if (activity.activity_type === "exam_activity") {
                entry.innerHTML = `<strong>Type:</strong> ${activity.activity_type}<br>
                                   <strong>Title:</strong> ${activity.title}<br>
                                   <strong>Score:</strong> ${activity.data.score}`;
            } else {
                entry.innerHTML = `<strong>Title:</strong> ${activity.title}<br>
                                   <strong>Score:</strong> No data available`;
            }

            scoreContainer.appendChild(entry);
        });
    }
})();
```

## 声明

（叠甲x）本插件作为学习使用，造成的一切后果均由使用人承担，本人概不负责
