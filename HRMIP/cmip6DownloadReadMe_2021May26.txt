# === readme ===

# descrip: instruction on how to download CMIP6 data from ESGF

# update history:
# v1.0 DL 2021May27

# extra notes:
# cmip6 downloading site(important): https://esgf-node.llnl.gov/search/cmip6/
# CMIP5 experiment design(recommended): https://portal.enes.org/data/enes-model-data/cmip5/datastructure
# cmip5 variables and meta data list: https://pcmdi.llnl.gov/mips/cmip3/variableList.html
# download esgf data with globus: https://www.youtube.com/watch?v=eZxuNMaA0ME
# access CMIP6 data: https://pcmdi.llnl.gov/CMIP6/Guide/dataUsers.html#3-accessing-model-output
# ESGF(https://esgf-node.llnl.gov/search/cmip6/) HRMIP does not have daily SSH(zos), only monthly zos (SSH) is available.  
# ECMWF and MPI do not have hires-future (2015-2050) zos data sets. There are five HRMIP models available for zos future projection: 1 CESM, 2 HadGEM, 3 CNRM, 4 EC-Earth, 5 CMCC.  
# ==============

  

# steps to download cmip6 data:
1. find LR and HR models in Souce ID on the left pannel in the downloading page (https://esgf-node.llnl.gov/search/cmip6/). Accoring to the presentation screenshot from Gaopeng, there are 7 models on ESGF with LR and HR outputs: 1. CESM, 2. HadGEM, 3. ECMWF, 4. CNRM, 5. EC-Earth, 6 CMCC, 7. MPI. To search models, e.g., HadGEM, search keywords: CMIP6, HadGEM3-GC31-HH (HadGEM3-GC31-LL), zos, highres-future, hist-1950.

2. download wget scripts from the specific data sets. I prefer to use wget than globus because I can use wget scripts as a record and modify it to download certain files (e.g., I can delete file names in the wget file list to download certain years of files instead of all year files). 

3. upload the wget scripts to grace and log in to data transfer nodes (1.ssh dapengli@grace.tamue.edu to enter the login nodes, 2.in login nodes, ssh grace-dtn1.hprc.tamu.edu to enter data transfer nodes, [dapengli@grace4 future]$ ssh grace-dtn2.hprc.tamu.edu).  

4. chmod u+x wget*.sh to add execute permission (/scratch and /ihesp dir have similar downloading speed according to Abishek).
[dapengli@dtn2 future]$ nohup ./wget-20210527231116.sh -H &
[1] 245284
[dapengli@dtn2 future]$ nohup: ignoring input and appending output to ‘nohup.out’
you must include -H, otherwise the wget scripts do not work (-H is for credential). nohup is to make sure the wget script is still running after you log out of the terminal.

5. you can ls to see downloading data files to cat nohup.out to view the log.  
