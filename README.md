# utl-extracting-text-from-single-strings-longer-that-k32-bytes
Extracting text from  single strings longer that k32 bytes

    Extracting text from  single strings longer that k32 bytes

    github
    https://tinyurl.com/y7elcg2p
    https://github.com/rogerjdeangelis/utl-extracting-text-from-single-strings-longer-that-k32-bytes

    SAS Forum
    https://tinyurl.com/yajp3ztp
    https://communities.sas.com/t5/SAS-Programming/Extracting-text-from-a-complex-string/m-p/523187

    Extract the quoted strings following '"column0":' in the long string

    INPUT
    =====

    String wrapped for easy viewing

    {"rows":{"row2":{"column0":"Nursing Facility Care","column1":"Hospital Leave Days",
    "column2":"N\/A","column3":"7","column4":"Days","column5":"1","column6":"Per Week",
    "column7":"activity","column8":"","column9":"","column10":""},"row3":{"column0":
    "Nursing Facility Care","column1":"Hospital Leave Days","column2":"N\/A",
    "column3":"7","column4":"Days","column5":"1","column6":"Per Week"
    ,"column7":"activity","column8":"","column9":"","column10":""}}}
    {"rows":{"row2":{"column0":"IRF Facility Care","column1":"Hospital Leave Days",
    "column2":"N\/A","column3":"7","column4":"Days","column5":"1","column6":"Per Week",
    "column7":"activity","column8":"","column9":"","column10":""},"row3":{"column0":
    "Nursing Facility Care","column1":"Hospital Leave Days","column2":"N\/A",
    "column3":"7","column4":"Days","column5":"1","column6":"Per Week"
    ,"column7":"activity","column8":"","column9":"","column10":""}}}
    {"rows":{"row2":{"column0":"Home Nursing Facility Care","column1":"Hospital Leave Days",
    "column2":"N\/A","column3":"7","column4":"Days","column5":"1","column6":"Per Week",
    "column7":"activity","column8":"","column9":"","column10":""},"row3":{"column0":
    "Nursing Facility Care","column1":"Hospital Leave Days","column2":"N\/A",
    "column3":"7","column4":"Days","column5":"1","column6":"Per Week"
    ,"column7":"activity","column8":"","column9":"","column10":""}}}


    EXAMPLE OUTPUT
    --------------

     WORK.WANT total obs=3

       Obs                STR

        1     "Nursing Facility Care"
        2     "IRF Facility Care"
        3     "Home Nursing Facility Care"


    PROCESS
    =======

    data want(where=(str ne '')); /* you dont need this is string is unrapped? */
    infile cards4 dlm=',';
    informat str $64.;
    input @'"column0":' str @@;
    cards4;
    {"rows":{"row2":{"column0":"Nursing Facility Care","column1":"Hospital Leave Days",
    "column2":"N\/A","column3":"7","column4":"Days","column5":"1","column6":"Per Week",
    "column7":"activity","column8":"","column9":"","column10":""},"row3":{"column0":
    "Nursing Facility Care","column1":"Hospital Leave Days","column2":"N\/A",
    "column3":"7","column4":"Days","column5":"1","column6":"Per Week"
    ,"column7":"activity","column8":"","column9":"","column10":""}}}
    {"rows":{"row2":{"column0":"IRF Facility Care","column1":"Hospital Leave Days",
    "column2":"N\/A","column3":"7","column4":"Days","column5":"1","column6":"Per Week",
    "column7":"activity","column8":"","column9":"","column10":""},"row3":{"column0":
    "Nursing Facility Care","column1":"Hospital Leave Days","column2":"N\/A",
    "column3":"7","column4":"Days","column5":"1","column6":"Per Week"
    ,"column7":"activity","column8":"","column9":"","column10":""}}}
    {"rows":{"row2":{"column0":"Home Nursing Facility Care","column1":"Hospital Leave Days",
    "column2":"N\/A","column3":"7","column4":"Days","column5":"1","column6":"Per Week",
    "column7":"activity","column8":"","column9":"","column10":""},"row3":{"column0":
    "Nursing Facility Care","column1":"Hospital Leave Days","column2":"N\/A",
    "column3":"7","column4":"Days","column5":"1","column6":"Per Week"
    ,"column7":"activity","column8":"","column9":"","column10":""}}}
    ;;;;
    run;quit;


