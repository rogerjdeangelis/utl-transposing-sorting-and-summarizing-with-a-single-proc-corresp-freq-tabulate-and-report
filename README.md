# utl-transposing-sorting-and-summarizing-with-a-single-proc-corresp-freq-tabulate-and-report
utl-transposing-sorting-and-summarizing-with-a-single-proc-corresp-freq-tabulate-and-report
    Transposing-sorting-and-summarizing-with-a-single-procs-corresp-freq-tabulate-and-report                                           
                                                                                                                                       
    All the techniques create an output sas table                                                                                      
                                                                                                                                       
    github                                                                                                                             
    https://tinyurl.com/yy7ddbnc                                                                                                       
    https://github.com/rogerjdeangelis/utl-transposing-sorting-and-summarizing-with-a-single-proc-corresp-freq-tabulate-and-report     
                                                                                                                                       
    related repos                                                                                                                      
    https://tinyurl.com/y65rk8rj                                                                                                       
    https://github.com/rogerjdeangelis?tab=repositories&q=transpose+summarize&type=&language=                                          
                                                                                                                                       
    SAS Forum                                                                                                                          
    https://tinyurl.com/y5vr9he9                                                                                                       
    https://communities.sas.com/t5/SAS-Programming/Transpose-character-data-wide/m-p/675142                                            
                                                                                                                                       
    https://communities.sas.com/t5/SAS-Programming/Transpose-character-data-wide/m-p/675142                                            
                                                                                                                                       
         Methods  (they all creat SAS table output)                                                                                    
                                                                                                                                       
           a. proc corresp                                                                                                             
           b. proc report                                                                                                              
           c. proc freq                                                                                                                
           d. proc tabulate                                                                                                            
                                                                                                                                       
        Note The original work for b, c, and d  was done by                                                                            
        Bartosz Jablonski                                                                                                              
        yabwon@gmail.com                                                                                                               
                                                                                                                                       
    /*                   _                                                                                                             
    (_)_ __  _ __  _   _| |_                                                                                                           
    | | `_ \| `_ \| | | | __|                                                                                                          
    | | | | | |_) | |_| | |_                                                                                                           
    |_|_| |_| .__/ \__,_|\__|                                                                                                          
            |_|                                                                                                                        
    */                                                                                                                                 
                                                                                                                                       
    WORK.HAVE total obs=6                                                                                                              
                                                                                                                                       
      STUDYID     DRUGS                                                                                                                
                                                                                                                                       
      ID-1-RMC    Opioid                                                                                                               
      ID-2-RMC    None                                                                                                                 
      ID-3-RMC    Benzo                                                                                                                
      ID-4-RMC    Cocaine                                                                                                              
      ID-4-RMC    Opioid                                                                                                               
      ID-5-RMC    Meth                                                                                                                 
                                                                                                                                       
                                                                                                                                       
    /*           _               _                                                                                                     
      ___  _   _| |_ _ __  _   _| |_                                                                                                   
     / _ \| | | | __| `_ \| | | | __|                                                                                                  
    | (_) | |_| | |_| |_) | |_| | |_                                                                                                   
     \___/ \__,_|\__| .__/ \__,_|\__|                                                                                                  
                    |_|                                                                                                                
      __ _      ___ ___  _ __ _ __ ___  ___ _ __                                                                                       
     / _` |    / __/ _ \| `__| `__/ _ \/ __| `_ \                                                                                      
    | (_| |_  | (_| (_) | |  | | |  __/\__ \ |_) |                                                                                     
     \__,_(_)  \___\___/|_|  |_|  \___||___/ .__/                                                                                      
                                           |_|                                                                                         
    */                                                                                                                                 
                                                                                                                                       
                                                                                                                                       
    WANT_CORRESP total obs=6                                                                                                           
                                                                                                                                       
     LABEL       BENZO    COCAINE    METH    NONE    OPIOID    SUM                                                                     
                                                                                                                                       
     ID-1-RMC      0         0         0       0        1       1                                                                      
     ID-2-RMC      0         0         0       1        0       1                                                                      
     ID-3-RMC      1         0         0       0        0       1                                                                      
     ID-4-RMC      0         1         0       0        1       2                                                                      
     ID-5-RMC      0         0         1       0        0       1                                                                      
     Sum           1         1         1       1        2       6                                                                      
                                                                                                                                       
    /*                                                                                                                                 
     _                                  _                                                                                              
    | |__     _ __ ___ _ __   ___  _ __| |_                                                                                            
    | `_ \   | `__/ _ \ `_ \ / _ \| `__| __|                                                                                           
    | |_) |  | | |  __/ |_) | (_) | |  | |_                                                                                            
    |_.__(_) |_|  \___| .__/ \___/|_|   \__|                                                                                           
                      |_|                                                                                                              
    */                                                                                                                                 
                                                                                                                                       
    WORK.WANT_RPT total obs=5                                                                                                          
                                                                                                                                       
     STUDYID     BENZO    COCAINE    METH    NONE    OPIOID                                                                            
                                                                                                                                       
     ID-1-RMC      0         0         0       0        1                                                                              
     ID-2-RMC      0         0         0       1        0                                                                              
     ID-3-RMC      1         0         0       0        0                                                                              
     ID-4-RMC      0         1         0       0        1                                                                              
     ID-5-RMC      0         0         1       0        0                                                                              
                                                                                                                                       
    /*         __                                                                                                                      
      ___     / _|_ __ ___  __ _                                                                                                       
     / __|   | |_| `__/ _ \/ _` |                                                                                                      
    | (__ _  |  _| | |  __/ (_| |                                                                                                      
     \___(_) |_| |_|  \___|\__, |                                                                                                      
                              |_|                                                                                                      
    */                                                                                                                                 
                                                                                                                                       
    Work.WANT_FRQ total obs=20                                                                                                         
                                                                                                                                       
      ROWNAM      LEVEL       BENZO    COCAINE      METH      NONE    OPIOID    TOTAL                                                  
                                                                                                                                       
      COUNT      ID-1-RMC      0.00       0.00      0.00      0.00      1.00     1.00                                                  
      PERCENT    ID-1-RMC      0.00       0.00      0.00      0.00     16.67    16.67                                                  
      ROW PCT    ID-1-RMC      0.00       0.00      0.00      0.00    100.00        0                                                  
      COL PCT    ID-1-RMC      0.00       0.00      0.00      0.00     50.00        0                                                  
      COUNT      ID-2-RMC      0.00       0.00      0.00      1.00      0.00     1.00                                                  
      PERCENT    ID-2-RMC      0.00       0.00      0.00     16.67      0.00    16.67                                                  
      ROW PCT    ID-2-RMC      0.00       0.00      0.00    100.00      0.00        0                                                  
      COL PCT    ID-2-RMC      0.00       0.00      0.00    100.00      0.00        0                                                  
      COUNT      ID-3-RMC      1.00       0.00      0.00      0.00      0.00     1.00                                                  
      PERCENT    ID-3-RMC     16.67       0.00      0.00      0.00      0.00    16.67                                                  
      ROW PCT    ID-3-RMC    100.00       0.00      0.00      0.00      0.00        0                                                  
      COL PCT    ID-3-RMC    100.00       0.00      0.00      0.00      0.00        0                                                  
      COUNT      ID-4-RMC      0.00       1.00      0.00      0.00      1.00     2.00                                                  
      PERCENT    ID-4-RMC      0.00      16.67      0.00      0.00     16.67    33.33                                                  
      ROW PCT    ID-4-RMC      0.00      50.00      0.00      0.00     50.00        0                                                  
      COL PCT    ID-4-RMC      0.00     100.00      0.00      0.00     50.00        0                                                  
      COUNT      ID-5-RMC      0.00       0.00      1.00      0.00      0.00     1.00                                                  
      PERCENT    ID-5-RMC      0.00       0.00     16.67      0.00      0.00    16.67                                                  
      ROW PCT    ID-5-RMC      0.00       0.00    100.00      0.00      0.00        0                                                  
      COL PCT    ID-5-RMC      0.00       0.00    100.00      0.00      0.00        0                                                  
                                                                                                                                       
                                                                                                                                       
    If you want counts then                                                                                                            
                                                                                                                                       
    data want_frqCnt;                                                                                                                  
      set WANT_FRQ(where=(ROWNAM="COUNT"));                                                                                            
    run;quit;                                                                                                                          
                                                                                                                                       
    WORK.WANT_FRQCNT total obs=5                                                                                                       
                                                                                                                                       
      ROWNAM     LEVEL      BENZO    COCAINE    METH    NONE    OPIOID    TOTAL                                                        
                                                                                                                                       
      COUNT     ID-1-RMC      0         0         0       0        1        1                                                          
      COUNT     ID-2-RMC      0         0         0       1        0        1                                                          
      COUNT     ID-3-RMC      1         0         0       0        0        1                                                          
      COUNT     ID-4-RMC      0         1         0       0        1        2                                                          
      COUNT     ID-5-RMC      0         0         1       0        0        1                                                          
                                                                                                                                       
                                                                                                                                       
    /*   _     _        _                                                                                                              
      __| |   | |_ __ _| |__                                                                                                           
     / _` |   | __/ _` | `_ \                                                                                                          
    | (_| |_  | || (_| | |_) |                                                                                                         
     \__,_(_)  \__\__,_|_.__/                                                                                                          
                                                                                                                                       
    */                                                                                                                                 
                                                                                                                                       
    * The J variables make it possible to remove                                                                                       
      the mutiple levels of spanning headers often present in tabulate output                                                          
      You will have to use '=""' to turn off all but the last row of column headers;                                                   
                                                                                                                                       
    from WANT_TAB total obs=5                                                                                                          
                                                                                                                                       
      J1STUDY_                                                                                                                         
         ID       J2BENZO    J3COCAINE    J4METH    J5NONE    J6OPIOID                                                                 
                                                                                                                                       
      ID-1-RMC       0           0           0         0          1                                                                    
      ID-2-RMC       0           0           0         1          0                                                                    
      ID-3-RMC       1           0           0         0          0                                                                    
      ID-4-RMC       0           1           0         0          1                                                                    
      ID-5-RMC       0           0           1         0          0                                                                    
                                                                                                                                       
                                                                                                                                       
    /*                                                                                                                                 
     _ __  _ __ ___   ___ ___  ___ ___  ___  ___                                                                                       
    | `_ \| `__/ _ \ / __/ _ \/ __/ __|/ _ \/ __|                                                                                      
    | |_) | | | (_) | (_|  __/\__ \__ \  __/\__ \                                                                                      
    | .__/|_|  \___/ \___\___||___/___/\___||___/                                                                                      
    |_|                                                                                                                                
      __ _      ___ ___  _ __ _ __ ___  ___ _ __                                                                                       
     / _` |    / __/ _ \| `__| `__/ _ \/ __| `_ \                                                                                      
    | (_| |_  | (_| (_) | |  | | |  __/\__ \ |_) |                                                                                     
     \__,_(_)  \___\___/|_|  |_|  \___||___/ .__/                                                                                      
                                           |_|                                                                                         
    */                                                                                                                                 
                                                                                                                                       
                                                                                                                                       
                                                                                                                                       
    data have;                                                                                                                         
     input StudyID $ Drugs $;                                                                                                          
    cards4;                                                                                                                            
    ID-1-RMC Opioid                                                                                                                    
    ID-2-RMC None                                                                                                                      
    ID-3-RMC Benzo                                                                                                                     
    ID-4-RMC Cocaine                                                                                                                   
    ID-4-RMC Opioid                                                                                                                    
    ID-5-RMC Meth                                                                                                                      
    ;;;;                                                                                                                               
    run;quit;                                                                                                                          
                                                                                                                                       
    proc datasets lib=work;                                                                                                            
     delete want_corresp;                                                                                                              
    run;quit;                                                                                                                          
                                                                                                                                       
    ods exclude all;                                                                                                                   
    ods output observed=want_corresp;                                                                                                  
    proc corresp data=have dim=1 observed;                                                                                             
     tables studyid, drugs;                                                                                                            
    run;quit;                                                                                                                          
    ods select all;                                                                                                                    
                                                                                                                                       
    /*                                                                                                                                 
     _                                  _                                                                                              
    | |__     _ __ ___ _ __   ___  _ __| |_                                                                                            
    | `_ \   | `__/ _ \ `_ \ / _ \| `__| __|                                                                                           
    | |_) |  | | |  __/ |_) | (_) | |  | |_                                                                                            
    |_.__(_) |_|  \___| .__/ \___/|_|   \__|                                                                                           
                      |_|                                                                                                              
    */                                                                                                                                 
                                                                                                                                       
    proc datasets lib=work;                                                                                                            
     delete want_rpt;                                                                                                                  
    run;quit;                                                                                                                          
                                                                                                                                       
    %utl_odsrpt(setup);                                                                                                                
    options missing="0";                                                                                                               
    proc report data=have nowd missing noheader formchar="|" box;                                                                      
    * note proc report cross columnes are always in sort order;                                                                        
    title "|STUDYID|Benzo|Cocaine|Meth|None|Opioid";                                                                                   
    cols studyId Drugs;                                                                                                                
    define studyid / group;                                                                                                            
    define drugs / across;                                                                                                             
    run;quit;                                                                                                                          
    %utl_odsrpt(outdsn=want_rpt);                                                                                                      
                                                                                                                                       
                                                                                                                                       
    /*         __                                                                                                                      
      ___     / _|_ __ ___  __ _                                                                                                       
     / __|   | |_| `__/ _ \/ _` |                                                                                                      
    | (__ _  |  _| | |  __/ (_| |                                                                                                      
     \___(_) |_| |_|  \___|\__, |                                                                                                      
                              |_|                                                                                                      
    */                                                                                                                                 
    proc datasets lib=work;                                                                                                            
     delete want_frq;                                                                                                                  
    run;quit;                                                                                                                          
                                                                                                                                       
    %utl_odsfrq(setup);                                                                                                                
    options formchar="|";                                                                                                              
    proc freq data=have ;                                                                                                              
    tables studyId*Drugs;                                                                                                              
    run;quit;                                                                                                                          
    %utl_odsfrq(outdsn=want_frq);                                                                                                      
                                                                                                                                       
                                                                                                                                       
    /*   _     _        _                                                                                                              
      __| |   | |_ __ _| |__                                                                                                           
     / _` |   | __/ _` | `_ \                                                                                                          
    | (_| |_  | || (_| | |_) |                                                                                                         
     \__,_(_)  \__\__,_|_.__/                                                                                                          
                                                                                                                                       
    */                                                                                                                                 
                                                                                                                                       
    proc datasets lib=work;                                                                                                            
     delete want_frq;                                                                                                                  
    run;quit;                                                                                                                          
                                                                                                                                       
    %utl_odstab(setup);                                                                                                                
    options formchar="|";                                                                                                              
    proc tabulate data=have ;                                                                                                          
    class studyid drugs;                                                                                                               
    table studyId="", Drugs=""*(n="")*f=10. /rts=20 box="Study_id";                                                                    
    run;quit;                                                                                                                          
    %utl_odstab(outdsn=want_tab);                                                                                                      
                                                                                                                                       
                                                                                                                                       
