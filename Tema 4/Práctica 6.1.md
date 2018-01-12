
~~~
---------------------------------
## ALTER SESSION
---------------------------------

ALTER SESSION SET NLS_DATE_FORMAT='DD/MM/YYYY';


---------------------------------
## BORRAR TABLAS ANTIGUAS
---------------------------------
DROP TABLE CENTROS CASCADE CONSTRAINTS;
DROP TABLE DEPARTAMENTOS CASCADE CONSTRAINTS;
DROP TABLE EMPLEADOS CASCADE CONSTRAINTS;

---------------------------------
## CREAR TABLAS
---------------------------------
create table CENTROS(
	NUMCE NUMBER(4),  
	NOMCE VARCHAR2(25),  
	DIRCE VARCHAR2(25),  
	CONSTRAINT CENTROS_PK PRIMARY KEY (NUMCE)   
);

create table DEPARTAMENTOS(
	NUMDE NUMBER(3),
	NUMCE NUMBER(4),
	DIREC NUMBER(3),
	TIDIR CHAR(1) CHECK (TIDIR IN('P', 'F')),
	PRESU NUMBER(3,1),
	DEPDE NUMBER(3),
	NOMDE VARCHAR2(20),
	CONSTRAINT DEPARTAMENTOS_PK PRIMARY KEY(NUMDE),
	FOREIGN KEY (NUMCE) REFERENCES CENTROS (NUMCE)
);

ALTER TABLE DEPARTAMENTOS ADD
FOREIGN KEY (DEPDE) REFERENCES DEPARTAMENTOS (NUMDE);

create table EMPLEADOS(
	NUMEM NUMBER(3) PRIMARY KEY,
	EXTEL NUMBER(3),
	FECNA DATE,
	FECIN DATE,
	SALAR NUMBER(5),
	COMIS NUMBER(3),
	NUMHI NUMBER(1),
	NOMEM VARCHAR2(10),
	NUMDE NUMBER(3),
	FOREIGN KEY (NUMDE) REFERENCES DEPARTAMENTOS (NUMDE)
);


---------------------------------
## INSERTAR DATOS
---------------------------------

-- CENTROS (Numce, Nomce, Se�as)
INSERT INTO CENTROS VALUES(10, 'SEDE CENTRAL', 'C/ATOCHA, 820, MADRID');
INSERT INTO CENTROS VALUES(20, 'RELACION CON CLIENTES', 'C/ATOCHA, 405, MADRID');


-- DEPARTAMENTOS (numde, numce, direc, tidir, presu, depde, nomde)
INSERT INTO DEPARTAMENTOS VALUES(100, 10, 260, 'P', 72, NULL, 'DIRECCI�N GENERAL');
INSERT INTO DEPARTAMENTOS VALUES(110, 20, 180, 'P', 90, 100, 'DIRECC.COMERCIAL');
INSERT INTO DEPARTAMENTOS VALUES(111, 20, 180, 'F', 66, 110, 'SECTOR INDUSTRIAL');
INSERT INTO DEPARTAMENTOS VALUES(112, 20, 270, 'P', 54, 110, 'SECTOR SERVICIOS');
INSERT INTO DEPARTAMENTOS VALUES(120, 10, 150, 'F', 18, NULL, 'ORGANIZACI�N');
INSERT INTO DEPARTAMENTOS VALUES(121, 10, 150, 'P', 12, 120, 'PERSONAL');
INSERT INTO DEPARTAMENTOS VALUES(122, 10, 350, 'P', 36, 120, 'PROCESO DE DATOS');
INSERT INTO DEPARTAMENTOS VALUES(130, 10, 310, 'P', 12, 100, 'FINANZAS');

-- EMPLEADOS (Numem, Extel, Fecna, Fecin, Salar, Comis, Numhi, Nomem, Numde)
INSERT INTO EMPLEADOS VALUES(110, 350, '10/11/1970', '15/02/1985', 1800, NULL, 3,'CESAR', 121);
INSERT INTO EMPLEADOS VALUES(120, 840, '09/06/1968', '01/10/1988', 1900, 110,  1,'MARIO', 112);
INSERT INTO EMPLEADOS VALUES(130, 810, '09/09/1965', '01/02/1981', 1500, 110,  2,'LUCIANO', 112);
INSERT INTO EMPLEADOS VALUES(150, 340, '10/08/1972', '15/01/1997', 2600, NULL, 0,'JULIO', 121);
INSERT INTO EMPLEADOS VALUES(160, 740, '09/07/1980', '11/11/2005', 1800, 110,  2,'AUREO', 111);
INSERT INTO EMPLEADOS VALUES(180, 508, '18/10/1974', '18/03/1996', 2800, 50,   2,'MARCOS', 110);
INSERT INTO EMPLEADOS VALUES(190, 350, '12/05/1972', '11/02/1992', 1750, NULL, 4,'JULIANA', 121);
INSERT INTO EMPLEADOS VALUES(210, 200, '28/09/1970', '22/01/1999', 1910, NULL, 2,'PILAR', 100);
INSERT INTO EMPLEADOS VALUES(240, 760, '26/02/1967', '24/02/1989', 1700, 100,  3,'LAVINIA', 111);
INSERT INTO EMPLEADOS VALUES(250, 250, '27/10/1976', '01/03/1997', 2700, NULL, 0,'ADRIANA', 100);
INSERT INTO EMPLEADOS VALUES(260, 220, '03/12/1973', '12/07/2001', 720,  NULL, 6,'ANTONIO', 100);
INSERT INTO EMPLEADOS VALUES(270, 800, '21/05/1975', '10/09/2003', 1910, 80,   3,'OCTAVIO', 112);
INSERT INTO EMPLEADOS VALUES(280, 410, '10/01/1978', '08/10/2010', 1500, NULL, 5,'DOROTEA', 130);
INSERT INTO EMPLEADOS VALUES(285, 620, '25/10/1979', '15/02/2011', 1910, NULL, 0,'OTILIA', 122);
INSERT INTO EMPLEADOS VALUES(290, 910, '30/11/1967', '14/02/1988', 1790, NULL, 3,'GLORIA', 120);
INSERT INTO EMPLEADOS VALUES(310, 480, '21/11/1976', '15/01/2001', 1950, NULL, 0,'AUGUSTO', 130);
INSERT INTO EMPLEADOS VALUES(320, 620, '25/12/1977', '05/02/2003', 2400, NULL, 2,'CORNELIO', 122);
INSERT INTO EMPLEADOS VALUES(330, 850, '19/08/1958', '01/03/1980', 1700, 90,   0,'AMELIA', 112);
INSERT INTO EMPLEADOS VALUES(350, 610, '13/04/1979', '10/09/1999', 2700, NULL, 1,'AURELIO', 122);
INSERT INTO EMPLEADOS VALUES(360, 750, '29/10/1978', '10/10/1998', 1800, 100,  2,'DORINDA', 111);
INSERT INTO EMPLEADOS VALUES(370, 360, '22/06/1977', '20/01/2000', 1860, NULL, 1,'FABIOLA', 121);
INSERT INTO EMPLEADOS VALUES(380, 880, '30/03/1978', '01/01/1999', 1100, NULL, 0,'MICAELA', 112);
INSERT INTO EMPLEADOS VALUES(390, 500, '19/02/1976', '08/10/2010', 1290, NULL, 1,'CARMEN', 110);
INSERT INTO EMPLEADOS VALUES(400, 780, '18/08/1979', '01/11/2011', 1150, NULL, 0,'LUCRECIA', 111);
INSERT INTO EMPLEADOS VALUES(410, 660, '14/07/1968', '13/10/1989', 1010, NULL, 0,'AZUCENA', 122);
INSERT INTO EMPLEADOS VALUES(420, 450, '22/10/1966', '19/11/1988', 2400, NULL, 0,'CLAUDIA', 130);
INSERT INTO EMPLEADOS VALUES(430, 650, '26/10/1967', '19/11/1988', 1260, NULL, 1,'VALERIANA', 122);
INSERT INTO EMPLEADOS VALUES(440, 760, '26/09/1966', '28/02/1986', 1260, 100,  0,'LIVIA', 111);
INSERT INTO EMPLEADOS VALUES(450, 880, '21/10/1966', '28/02/1986', 1260, 100,  0,'SABINA', 112);
INSERT INTO EMPLEADOS VALUES(480, 760, '04/04/1965', '28/02/1986', 1260, 100,  1,'DIANA', 111);
INSERT INTO EMPLEADOS VALUES(490, 880, '06/06/1964', '01/01/1988', 1090, 100,  0,'HORACIO', 112);
INSERT INTO EMPLEADOS VALUES(500, 750, '08/10/1965', '01/01/1987', 1200, 100,  0,'HONORIA', 111);
INSERT INTO EMPLEADOS VALUES(510, 550, '04/05/1966', '01/11/1986', 1200, NULL, 1,'ROMULO', 110);
INSERT INTO EMPLEADOS VALUES(550, 780, '10/01/1970', '21/01/1998', 600,  120,  0,'SANCHO', 111);


-----------------------------
## CONSULTAS SENCILLAS
-----------------------------

-- 1. Departamentos con director en funciones.

SELECT D.NOMDE
FROM DEPARTAMENTOS D
WHERE TIDIR = 'F'
order by D.NOMDE;

-- 2. Teléfonos de empleados del departamento 121.

SELECT E.NOMEM, E.NUMEM, E.EXTEL
FROM EMPLEADOS E
WHERE E.NUMDE = 121
order by E.NOMEM;

-- 3. Extención teléfonica de los empleados del departamento 121.

SELECT E.NOMEM "Nombre", E.EXTEL "Extensión Teléfonica"
FROM EMPLEADOS E
WHERE E.NUMDE = 110
order by E.EXTEL;

-- 4. Comisión, nombre y salario de los empleados que tienen tres hijos.

SELECT E.COMIS, E.NOMEM, E.SALAR
FROM EMPLEADOS E
WHERE NUMHI = 3
order by E.COMIS, E.NOMEM;

-- 5. Comisión, nombre y salario de los empleados que tienen tres hijos, y tiene comisión.

SELECT E.COMIS, E.NOMEM, E.SALAR
FROM EMPLEADOS E
WHERE NUMHI = 3 AND E.COMIS is not null
order by E.COMIS;

-- 6. Salario y nombre de los empleados sin hijos y cuyo salario es mayor que 1200 y menor que 1500 €.

SELECT SALAR, NOMEM
FROM EMPLEADOS
WHERE NUMHI = 0 AND SALAR > 1200 AND SALAR < 1500
order by SALAR DESC, NOMEM;

-- 7. Números de los departamentos donde trabajan empleados cuyo salario sea inferior a 1500 €.

SELECT DISTINCT NUMDE
FROM empleados 
WHERE SALAR < 1500
order by 1;

-- 8. Obtener las distintas comisiones que hay en el departamento 110.

SELECT DISTINCT comis
FROM empleados
WHERE numde = 110 AND comis is not null
order by 1;

------------------------------
## CONSULTAS CON PREDICADOS BÁSICOS
------------------------------

-- 1. Departamentos cuyo presupuesto es inferior a 30.000 €.

SELECT 'DEPARTAMENTO DE ' || nomde AS "NOMBRE"
FROM DEPARTAMENTOS
WHERE presu < 30
ORDER BY 1; 

-- 2. Número y nombre de departamento separados por guión, ademas de el tipo de director de aquellos departamentos con presupuesto inferior a 30000.

SELECT numde ||'-'|| nomde AS "Número-nombre", 
  tidir AS "Tipo de Director"
FROM DEPARTAMENTOS
WHERE presu < 30
ORDER BY 1; 

-- 3. Empleados con más de 4 hijos su nombre y su sueldo anual, actual y para cada uno de los próximos dos años.

SELECT nomem "Nombre", 12*salar AS "Salario 2014", 
  12*1.02*salar AS "Salario 2015", 
  12*1.02*1.02*salar AS "Salario 2016"
FROM EMPLEADOS
WHERE numhi > 4
ORDER BY 1; 

-- 4. 

SELECT nomem
FROM EMPLEADOS
WHERE 120*numhi > 0.2*salar
ORDER BY 1; 

-- 5

SELECT nomem AS "NOMBRE", salar+comis AS "SALARIO TOTAL"
FROM EMPLEADOS
WHERE numde = 112
ORDER BY 2 DESC, 1; 

-- 6

SELECT nomem AS "NOMBRE", salar+NVL(comis, 0) AS "SALARIO TOTAL"
FROM EMPLEADOS
WHERE numde = 112 
ORDER BY 2 DESC, 1 ASC; 

-- 7

SELECT nomem AS "NOMBRE", salar+NVL(comis, 0)|| ' €' AS "SALARIO TOTAL"
FROM EMPLEADOS
WHERE numde = 112 
ORDER BY 2 DESC, 1 ASC; 

-- 8

SELECT nomem AS "NOMBRE",
Salar+60*(numhi-3) || ' €' AS "SALARIO TOTAL"
FROM EMPLEADOS
WHERE numhi >= 4
ORDER BY 1; 

-- 9

SELECT nomem AS "NOMBRE", 
  salar+60*(numhi-3) || ' €' AS "SALARIO TOTAL"
FROM EMPLEADOS
WHERE numhi >= (SELECT numhi
                FROM EMPLEADOS
                WHERE nomem='JULIANA')
ORDER BY 1; 

-- 10

SELECT nomem
FROM EMPLEADOS
WHERE salar >= 1.15*(SELECT salar
                     FROM EMPLEADOS
                     WHERE nomem='CLAUDIA')
ORDER BY 1;

-- otra forma de hacerlo:

SELECT nomem
FROM EMPLEADOS
WHERE salar >=(SELECT 1.15*salar
               FROM EMPLEADOS
               WHERE nomem='CLAUDIA')
ORDER BY 1; 

-- 11

SELECT nomde
FROM DEPARTAMENTOS
WHERE depde IS NULL; 

-----------------------------------------------------------
## Consultas con Predicados Cuantificados: ALL, SOME o ANY.
-----------------------------------------------------------

-- 1

SELECT nomem
FROM EMPLEADOS
WHERE salar >ALL (SELECT salar
                  FROM EMPLEADOS
                  WHERE numde=122)
ORDER BY 1; 

-- 2

SELECT nomem
FROM EMPLEADOS
WHERE salar >ALL (SELECT salar
                  FROM EMPLEADOS
                  WHERE numde=150)
ORDER BY 1; 

-- 3

SELECT nomem
FROM EMPLEADOS
WHERE salar >SOME (SELECT 2.5*salar
                   FROM EMPLEADOS
                   WHERE numde=122)
ORDER BY 1; 

-- 4

SELECT nomem, salar
FROM EMPLEADOS
WHERE salar =SOME (SELECT comis*10 FROM EMPLEADOS); 

-- 5

SELECT nomem, salar
FROM EMPLEADOS
WHERE salar >ALL (SELECT comis*20
                  FROM EMPLEADOS
                  WHERE comis IS NOT NULL)
ORDER BY 1; 

-- 6

SELECT nomem, salar
FROM EMPLEADOS
WHERE salar <ALL (SELECT 20*comis
                  FROM EMPLEADOS
                  WHERE comis IS NOT NULL)
ORDER BY 1; 

-----------------------------------
## Consultas con Predicados BETWEEN 
-----------------------------------

-- 1

SELECT nomem
FROM EMPLEADOS
WHERE salar BETWEEN 1500 AND 1600
ORDER BY 1;

-- 2

SELECT nomem, salar
FROM EMPLEADOS
WHERE comis is not null AND salar NOT BETWEEN numhi*720 AND comis*50*numhi
ORDER BY 1;

------------------------
## LIKE
------------------------

-- 1

SELECT nomem "Nombre", salar || '€' AS "Salario" 
FROM EMPLEADOS
WHERE nomem LIKE 'A%'
ORDER BY 1;

-- 2

SELECT nomem 
FROM EMPLEADOS
WHERE nomem LIKE '________'
ORDER BY 1;

-- 3

SELECT 'DEPARTAMENTO DE ' || nomde AS "Departamento", presu ||'.000' || '€' AS "Presupuesto"
FROM DEPARTAMENTOS
WHERE nomde LIKE '%SECTOR%'
ORDER BY 1;

-------------------------------
## Consultas con Predicados IN
-------------------------------

-- 1

SELECT nomem
FROM EMPLEADOS
WHERE extel IN (250, 750)
ORDER BY 1;

-- 2

SELECT nomem 
FROM EMPLEADOS
WHERE numde IN (SELECT numde
               FROM EMPLEADOS
               WHERE nomem IN('PILAR', 'DOROTEA'))
ORDER BY 1;

-- 3

SELECT nomde "Nombres Departamentos", direc "Identificador de su director"
FROM DEPARTAMENTOS
WHERE direc IN (SELECT direc
                FROM DEPARTAMENTOS
                WHERE nomde IN('DIRECC.COMERCIAL', 'PERSONAL'))
ORDER BY 2 DESC;

----------------------------------
## Consultas con Predicados EXISTS
----------------------------------

-- 1

SELECT nomce
FROM CENTROS
WHERE EXISTS (SELECT *
             FROM CENTROS
             WHERE dirce LIKE '%ATOCHA%');
			 
-- 2
	
SELECT nomem, salar
FROM empleados
WHERE numde = 100 
AND EXISTS (SELECT *
             FROM empleados
             WHERE numde = 100 AND salar > 1300);

-- 3			 

SELECT nomem, salar
FROM empleados
WHERE numde = 100
AND EXISTS (SELECT *
            FROM EMPLEADOS
            WHERE numde = 100 AND salar > 2750);
			
~~~ .sql
SELECT nomem, salar
FROM empleados
WHERE numde = 100
AND EXISTS (SELECT *
           FROM empleados
           WHERE numde = 100 AND salar > 3000);
~~~
----------------------------------
## Más Consultas con Predicados
----------------------------------

-- 1

SELECT nomem, comis
FROM EMPLEADOS
WHERE numde = 110 
AND EXISTS (SELECT * 
	        FROM EMPLEADOS
			WHERE numde = 110 AND comis is not null)
ORDER BY 1;

-- 2

SELECT nomde 
FROM DEPARTAMENTOS
WHERE nomde NOT LIKE 'SECTOR%' AND nomde NOT LIKE 'DIRECC%';

-- 3

SELECT nomem "NOMBRE", salar || '€' AS "SALARIO"
FROM EMPLEADOS
WHERE (numhi = 0 AND salar > 1500) OR (numhi != 0 AND salar<1000)
ORDER BY 1;

-- 4

SELECT 'nº'|| numem AS "NÚMERO EMPLEADO", nomem "NOMBRE", salar+comis || '€' AS "SALARIO TOTAL"
FROM EMPLEADOS
WHERE (salar+comis)>= 1800;

-- 5

SELECT nomem, salar
FROM empleados
WHERE numde = 111 AND comis > 0 
AND EXISTS (SELECT *
           FROM empleados
           WHERE comis > ((salar * 15) /100))
ORDER BY 1;

-- 6

SELECT nomde "Nombre de Departamento", tidir "Tipo director", presu "Presupuesto"
FROM departamentos
WHERE presu > 30 or depde is null;

-- 7

SELECT nomde "Nombre de Departamento", tidir "Tipo director", presu || '.000' AS "Presupuesto"
FROM departamentos
WHERE presu > 30 or depde is null;
~~~





