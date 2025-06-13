

cap log close 
*make a new logfile for this dofile / session
log using do/first_week.txt, text replace 

import delimited data/one_crop_owners.csv, clear

// the following IV analysis is for farmers who only grow one crop.

//summary

sum total_livestock livestock_died_total burns_crop_1

sum total_livestock livestock_died_total burns_crop_1 if year ==2018


// first stage
reg total_livestock livestock_died_total, robust

// 2018 has the most number of observations, so filtering out other dates
reg total_livestock livestock_died_total if year == 2018, robust


ivreg2 burns_crop_1 (total_livestock = livestock_died_total), robust


ivreg2 burns_crop_1 (total_livestock = livestock_died_total) if year == 2018, robust



// the following is for farmers who grow more than one crop.

clear all

import delimited data/first_week.csv, clear



// summary

sum herd_size livestock_died_total crop_burning

sum herd_size livestock_died_total crop_burning if year ==2018



//first stage
reg herd_size livestock_died_total, robust

// again 2018 has the most no. of observations
reg herd_size livestock_died_total if year == 2018, robust


//ivreg
ivreg2 crop_burning (herd_size = livestock_died_total), robust

ivreg2 crop_burning (herd_size = livestock_died_total) if year == 2018, robust


log close




