-- lecture11 data science
-- MOHAMMAD ALHROOB

CREATE OR REPLACE FUNCTION get_last_day(p_date date) RETURN number 
IS  
p_day number(2); 
 
BEGIN 
p_day :=  CAST(TO_CHAR(LAST_DAY( p_date), 'DD') AS INT); 
RETURN p_day; 
END;
/
CREATE OR REPLACE FUNCTION calcaute_saraly(p_date date ,p_salary number ) RETURN number   
 
IS 
p_total_salary number(10):=0 ; 
daily_salary number(10):=0; 
BEGIN  
daily_salary := p_salary / get_last_day(p_date); 
p_total_salary :=  daily_salary * EXTRACT(DAY from p_date); 
 
RETURN p_total_salary ;  
END;  
/
Select calcaute_saraly(Sysdate,1600) From Dual;
