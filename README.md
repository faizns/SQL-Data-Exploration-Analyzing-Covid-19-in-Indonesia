# 🌏 SQL Data Exploration: Analyzing Covid-19 in Indonesia

> **Tools** : PostgreSQL

## 🔎 Objective
Menganalisa data Covid-19 untuk menemukan insight, khususnya untuk mencari informasi mengenai kasus yang terkonfirmasi dan vaksinasi yang ada di Indonesia.

## 🔎 Dataset
Data covid Covid-19 dari 4 Februari 2020 hingga 22 November 2022 dari [Our World in Data](https://ourworldindata.org/covid-deaths). Dataset dibagi dalam 2 file csv yang meliputi :
- covid19_deaths.csv — berisi *record* kasus dan kematian Covid-19 di seluruh dunia
- covid19_vaccination — berisi informasi *record* Covid-19 di seluruh dunia

## 🔎 Analysis
### 1. Analisa Berdasarkan Lokasi
**Total Cases, Total Deaths, & Death Rate by Country and Date**
```postgresql
-- Seluruh Dunia
SELECT 
    location, 
    date, 
    total_cases, 
    total_deaths,
	(total_deaths/total_cases)*100 AS death_rate
FROM covid_deaths
WHERE continent IS NOT null
ORDER BY 1, 2
```
<p align="center">
  <kbd><img src="deathpercent_worldwide.png" width=600px> </kbd> <br>
   Gambar 1 — *Death Rate* merepresentasikan kemungkinan kematian akibat Covid-19. Dapat di lihat di Afganistan kematian mulai terjadi pada hari ke-8.
</p>


```postgresql
-- Indonesia
SELECT 
	location, 
	date, 
	total_cases, 
	total_deaths,
	(total_deaths/total_cases)*100 AS death_rate
FROM covid_deaths
WHERE LOCATION LIKE 'Indonesia'
ORDER BY 1, 2
```