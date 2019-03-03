# sql_percentage_calculator
Make percentage calculator using sql and compare between two column.

------------------------------------------------------------------

<h5>Calculation Of Find Percentage</h5>

suppose,
  we make two variable and give some value.</br>
    orgNumber=200;
    newNumber=120;
  
  now,
    1st calculation is (200-120)/200X100=%;</br>
    2nd calculation is (120/200)X100=%;</br>
    
    fNumber=200, sNumber=120
  
1st: CAST(round(((fNumber - sNumber)/fNumber * 100),2) AS DECIMAL(10,2)).</br>
2nd: CAST(round((sNumber/fNumber) * 100) AS DECIMAL(10,2)).

there,
CAST(data AS DECIMAL(10,2)),round(data,how_many_number_want_to_print).</br>
this all function we used for print float number like 12.2.

/*-------------//--------------------------------------------//------------------------*/

    SELECT strength, present, (strength-present) absent, ((strength - present)/strength * 100) abs_perchant, 
    (round((present/strength)*100))
    from
    (select count(cardno) strength 
     from tb_personal_info 
     where active=0),
    (select count(cardno) present 
     from tb_data_master
     where
    tb_data_master.pdate='18-JUL-18' 
    and tb_data_master.intime is not null 
    and tb_data_master.outtime is not null);

==>

    SELECT personalCard,dataCard,
    CAST(round(((personalCard - dataCard)/personalCard * 100),2) AS DECIMAL(10,2))
    from
    (select count(cardno) personalCard from tb_personal_info where active=0),
    (select count(cardno) dataCard from tb_data_master
    where
    tb_data_master.pdate='18-JUL-18' 
    and tb_data_master.intime is not null 
    and tb_data_master.outtime is not null);
    
For duplicate data.
    
    distinct
