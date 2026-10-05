# Indiana-ABA-Database-system

CREATE DATABASE Indiana_ABA_Provider_DB;
USE Indiana_ABA_Provider_DB;
CREATE TABLE Company
(
    CompanyID VARCHAR(4),
    CompanyName VARCHAR(100) NOT NULL,
    Website VARCHAR(150),
    Phone VARCHAR(20),
    Email VARCHAR(100),

    CONSTRAINT Company_CompanyID_PK
        PRIMARY KEY (CompanyID)
);
CREATE TABLE ClinicLocation
(
    LocationID VARCHAR(4),
    CompanyID VARCHAR(4),
    StreetAddress VARCHAR(150),
    City VARCHAR(40),
    County VARCHAR(40),
    ZipCode VARCHAR(10),

    CONSTRAINT ClinicLocation_LocationID_PK
        PRIMARY KEY (LocationID),

    CONSTRAINT ClinicLocation_CompanyID_FK
        FOREIGN KEY (CompanyID)
        REFERENCES Company(CompanyID)
);
CREATE TABLE Service
(
    ServiceID VARCHAR(4),
    ServiceName VARCHAR(60),

    CONSTRAINT Service_ServiceID_PK
        PRIMARY KEY(ServiceID)
);

CREATE TABLE CompanyService
(
    CompanyID VARCHAR(4),
    ServiceID VARCHAR(4),

    CONSTRAINT CompanyService_PK
        PRIMARY KEY(CompanyID,ServiceID),

    CONSTRAINT CompanyService_CompanyID_FK
        FOREIGN KEY(CompanyID)
        REFERENCES Company(CompanyID),

    CONSTRAINT CompanyService_ServiceID_FK
        FOREIGN KEY(ServiceID)
        REFERENCES Service(ServiceID)
);

CREATE TABLE Insurance
(
    InsuranceID VARCHAR(4),
    InsuranceName VARCHAR(50),

    CONSTRAINT Insurance_InsuranceID_PK
        PRIMARY KEY(InsuranceID)
);

CREATE TABLE CompanyInsurance
(
    CompanyID VARCHAR(4),
    InsuranceID VARCHAR(4),

    CONSTRAINT CompanyInsurance_PK
        PRIMARY KEY(CompanyID,InsuranceID),

    CONSTRAINT CompanyInsurance_CompanyID_FK
        FOREIGN KEY(CompanyID)
        REFERENCES Company(CompanyID),

    CONSTRAINT CompanyInsurance_InsuranceID_FK
        FOREIGN KEY(InsuranceID)
        REFERENCES Insurance(InsuranceID)
);

CREATE TABLE JobOpening
(
    JobID VARCHAR(4),
    CompanyID VARCHAR(4),
    JobTitle VARCHAR(50),
    EmploymentType VARCHAR(20),
    HourlyPay DECIMAL(6,2),
    DatePosted DATE,

    CONSTRAINT JobOpening_JobID_PK
        PRIMARY KEY(JobID),

    CONSTRAINT JobOpening_CompanyID_FK
        FOREIGN KEY(CompanyID)
        REFERENCES Company(CompanyID)
);

INSERT INTO Service VALUES
('S001','Clinic-Based ABA'),
('S002','Home-Based ABA'),
('S003','School-Based ABA'),
('S004','Parent Training'),
('S005','Diagnostic Assessment'),
('S006','Early Intervention'),
('S007','Social Skills Group'),
('S008','Telehealth');

INSERT INTO Insurance VALUES
('I001','Indiana Medicaid'),
('I002','Anthem BCBS'),
('I003','Aetna'),
('I004','Cigna'),
('I005','UnitedHealthcare'),
('I006','CareSource'),
('I007','Humana'),
('I008','MDwise'),
('I009','MHS'),
('I010','Tricare');

INSERT INTO Company VALUES
('C001','Hopebridge','https://www.hopebridge.com','317-555-1001','info@hopebridge.com'),

('C002','LittleStar ABA Therapy','https://www.littlestaraba.org','317-555-1002','info@littlestaraba.org'),

('C003','Bierman Autism Centers','https://www.biermanautism.com','317-555-1003','info@biermanautism.com'),

('C004','Lighthouse Autism Center','https://www.lighthouseautismcenter.com','317-555-1004','info@lighthouseautismcenter.com'),

('C005','Applied Behavior Center for Autism','https://www.appliedbehaviorcenter.org','317-555-1005','info@appliedbehaviorcenter.org'),

('C006','Circle City ABA','https://www.circlecityaba.com','317-555-1006','info@circlecityaba.com'),

('C007','Golden Steps ABA','https://www.goldenstepsaba.com','317-555-1007','info@goldenstepsaba.com'),

('C008','Adapt For Life','https://www.adaptforlife.org','317-555-1008','info@adaptforlife.org'),

('C009','Life Skills Autism Academy','https://www.lifeskillsautismacademy.com','317-555-1009','info@lifeskillsautismacademy.com'),

('C010','Damar ABA Services','https://www.damar.org','317-555-1010','info@damar.org'),

('C011','Magical Moments ABA','https://www.magicalmomentsaba.com','317-555-1011','info@magicalmomentsaba.com'),

('C012','Achievements ABA Therapy','https://www.achievementsaba.com','317-555-1012','info@achievementsaba.com'),

('C013','Elevation Autism Center','https://www.elevationautism.com','317-555-1013','info@elevationautism.com'),

('C014','Supportive Care ABA','https://www.supportivecareaba.com','317-555-1014','info@supportivecareaba.com'),

('C015','BridgeCare ABA','https://www.bridgecareaba.com','317-555-1015','info@bridgecareaba.com'),

('C016','Step Ahead ABA','https://www.stepaheadaba.com','317-555-1016','info@stepaheadaba.com'),

('C017','Above & Beyond ABA','https://www.aboveandbeyondaba.com','317-555-1017','info@aboveandbeyondaba.com'),

('C018','Crossroads ABA','https://www.crossroadsaba.com','317-555-1018','info@crossroadsaba.com'),

('C019','Compass ABA','https://www.compassaba.com','317-555-1019','info@compassaba.com'),

('C020','Bright Futures ABA','https://www.brightfuturesaba.com','317-555-1020','info@brightfuturesaba.com'),

('C021','Positive Pathways ABA','https://www.positivepathwaysaba.com','317-555-1021','info@positivepathwaysaba.com'),

('C022','Behavior Analysis Center for Autism','https://www.bacforautism.com','317-555-1022','info@bacforautism.com'),

('C023','Indiana Autism Center','https://www.indianaautismcenter.com','317-555-1023','info@indianaautismcenter.com'),

('C024','Autism Learning Partners','https://www.autismlearningpartners.com','317-555-1024','info@autismlearningpartners.com'),

('C025','Action Behavior Services','https://www.actionbehavior.com','317-555-1025','info@actionbehavior.com'),

('C026','Grateful Care ABA','https://www.gratefulcareaba.com','317-555-1026','info@gratefulcareaba.com'),

('C027','Illuminate ABA','https://www.illuminateaba.com','317-555-1027','info@illuminateaba.com'),

('C028','New Horizons ABA','https://www.newhorizonsaba.com','317-555-1028','info@newhorizonsaba.com'),

('C029','B Above Services','https://www.baboveservices.com','317-555-1029','info@baboveservices.com'),

('C030','Succeed ABA Therapy','https://www.succeedaba.com','317-555-1030','info@succeedaba.com');

/*=========================================================
 Part 2 - Clinic Locations
=========================================================*/

INSERT INTO ClinicLocation VALUES
('L001','C001','801 Congressional Blvd Suite 600','Carmel','Hamilton','46032'),
('L002','C001','21 S Park Blvd Suite 21','Greenwood','Johnson','46143'),
('L003','C001','160 Plainfield Village Dr Suite 101','Plainfield','Hendricks','46168'),
('L004','C001','2620 Kessler Blvd E Dr Suite 105','Indianapolis','Marion','46220'),
('L005','C001','9769 Crosspoint Blvd','Indianapolis','Marion','46256'),

('L006','C002','12650 Hamilton Crossing Blvd','Carmel','Hamilton','46032'),
('L007','C002','3850 Priority Way South Dr','Indianapolis','Marion','46240'),
('L008','C002','1400 Teal Rd','Lafayette','Tippecanoe','47905'),

('L009','C003','1022 E 52nd St','Indianapolis','Marion','46205'),
('L010','C003','6060 N College Ave','Indianapolis','Marion','46220'),
('L011','C003','5250 E US Highway 36 Suite 630','Avon','Hendricks','46123'),
('L012','C003','Fort Wayne Center','Fort Wayne','Allen','46825'),

('L013','C004','3435 W 96th St','Indianapolis','Marion','46268'),
('L014','C004','Noblesville Center','Noblesville','Hamilton','46060'),
('L015','C004','South Bend Center','South Bend','St. Joseph','46601'),
('L016','C004','Fort Wayne Center','Fort Wayne','Allen','46804'),
('L017','C004','Lafayette Center','Lafayette','Tippecanoe','47905'),

('L018','C005','13431 Old Meridian St','Carmel','Hamilton','46032'),
('L019','C005','12244 E 116th St','Fishers','Hamilton','46037'),
('L020','C005','7901 E 88th St','Indianapolis','Marion','46256'),
('L021','C005','5545 E Stop 11 Rd','Indianapolis','Marion','46237'),
('L022','C005','Greenwood Clinic','Greenwood','Johnson','46142'),

('L023','C006','5915 S Emerson Ave Suite 100','Indianapolis','Marion','46237'),
('L024','C006','West Lafayette Clinic','West Lafayette','Tippecanoe','47906'),
('L025','C006','Fishers Clinic','Fishers','Hamilton','46038'),

('L026','C007','Indianapolis West Clinic','Indianapolis','Marion','46234'),
('L027','C007','Fort Wayne Clinic','Fort Wayne','Allen','46805'),

('L028','C008','Fishers Clinic','Fishers','Hamilton','46038'),
('L029','C008','Carmel Clinic','Carmel','Hamilton','46032'),

('L030','C009','6855 Shore Terrace Suite 130','Indianapolis','Marion','46254'),
('L031','C009','Greenwood Clinic','Greenwood','Johnson','46143'),

('L032','C010','Indianapolis Clinic','Indianapolis','Marion','46222'),

('L033','C011','Beech Grove Clinic','Beech Grove','Marion','46107'),

('L034','C012','Fishers Clinic','Fishers','Hamilton','46038'),

('L035','C013','West Lafayette Clinic','West Lafayette','Tippecanoe','47906'),

('L036','C014','South Bend Clinic','South Bend','St. Joseph','46614'),

('L037','C015','Kokomo Clinic','Kokomo','Howard','46901'),

('L038','C016','Bloomington Clinic','Bloomington','Monroe','47401'),

('L039','C017','Columbus Clinic','Columbus','Bartholomew','47201'),

('L040','C018','Fort Wayne Clinic','Fort Wayne','Allen','46815'),

('L041','C019','Lafayette Clinic','Lafayette','Tippecanoe','47904'),

('L042','C020','Indianapolis South Clinic','Indianapolis','Marion','46227'),

('L043','C021','Greenwood Clinic','Greenwood','Johnson','46143'),

('L044','C022','Carmel Clinic','Carmel','Hamilton','46032'),

('L045','C023','Fishers Clinic','Fishers','Hamilton','46037'),

('L046','C024','West Lafayette Clinic','West Lafayette','Tippecanoe','47906'),

('L047','C025','Indianapolis East Clinic','Indianapolis','Marion','46219'),

('L048','C026','Fishers Clinic','Fishers','Hamilton','46038'),

('L049','C027','Beech Grove Clinic','Beech Grove','Marion','46107'),

('L050','C028','Noblesville Clinic','Noblesville','Hamilton','46060'),

('L051','C029','Lafayette Clinic','Lafayette','Tippecanoe','47905'),

('L052','C030','Fort Wayne Clinic','Fort Wayne','Allen','46835');

INSERT INTO CompanyService VALUES
('C001','S001'),('C001','S002'),('C001','S004'),('C001','S006'),
('C002','S001'),('C002','S002'),('C002','S007'),
('C003','S001'),('C003','S004'),('C003','S006'),
('C004','S001'),('C004','S002'),('C004','S008'),
('C005','S001'),('C005','S003'),('C005','S005'),
('C006','S001'),('C006','S002'),('C006','S007'),
('C007','S001'),('C007','S002'),
('C008','S001'),('C008','S002'),('C008','S008'),
('C009','S001'),('C009','S004'),
('C010','S001'),('C010','S003'),
('C011','S001'),('C011','S002'),
('C012','S001'),('C012','S004'),
('C013','S001'),('C013','S002'),
('C014','S001'),('C014','S003'),
('C015','S001'),('C015','S002'),
('C016','S001'),('C016','S007'),
('C017','S001'),('C017','S004'),
('C018','S001'),('C018','S002'),
('C019','S001'),('C019','S008'),
('C020','S001'),('C020','S002'),
('C021','S001'),('C021','S004'),
('C022','S001'),('C022','S005'),
('C023','S001'),('C023','S006'),
('C024','S001'),('C024','S002'),
('C025','S001'),('C025','S003'),
('C026','S001'),('C026','S004'),
('C027','S001'),('C027','S002'),
('C028','S001'),('C028','S006'),
('C029','S001'),('C029','S007'),
('C030','S001'),('C030','S002');

INSERT INTO CompanyInsurance VALUES
('C001','I001'),('C001','I002'),('C001','I003'),
('C002','I001'),('C002','I005'),
('C003','I002'),('C003','I003'),('C003','I004'),
('C004','I001'),('C004','I005'),
('C005','I001'),('C005','I002'),
('C006','I002'),('C006','I003'),
('C007','I001'),('C007','I006'),
('C008','I002'),('C008','I005'),
('C009','I001'),('C009','I009'),
('C010','I001'),('C010','I008'),
('C011','I001'),('C011','I002'),
('C012','I002'),('C012','I003'),
('C013','I001'),('C013','I005'),
('C014','I002'),('C014','I004'),
('C015','I001'),('C015','I010'),
('C016','I002'),('C016','I003'),
('C017','I001'),('C017','I002'),
('C018','I001'),('C018','I006'),
('C019','I003'),('C019','I005'),
('C020','I001'),('C020','I002'),
('C021','I001'),('C021','I007'),
('C022','I002'),('C022','I003'),
('C023','I001'),('C023','I008'),
('C024','I002'),('C024','I005'),
('C025','I001'),('C025','I003'),
('C026','I001'),('C026','I006'),
('C027','I002'),('C027','I005'),
('C028','I001'),('C028','I007'),
('C029','I001'),('C029','I002'),
('C030','I001'),('C030','I005');

INSERT INTO JobOpening VALUES
('J001','C001','RBT','Full-Time',24.50,'2026-06-01'),
('J002','C001','BCBA','Full-Time',42.00,'2026-06-03'),
('J003','C002','RBT','Full-Time',23.00,'2026-06-05'),
('J004','C003','RBT','Part-Time',22.00,'2026-06-06'),
('J005','C003','BCBA','Full-Time',45.00,'2026-06-07'),
('J006','C004','Behavior Therapist','Full-Time',21.50,'2026-06-08'),
('J007','C005','RBT','Full-Time',24.00,'2026-06-09'),
('J008','C006','RBT','Full-Time',23.50,'2026-06-10'),
('J009','C007','BCBA','Full-Time',44.00,'2026-06-11'),
('J010','C008','RBT','Part-Time',22.50,'2026-06-12'),
('J011','C009','Clinical Director','Full-Time',60.00,'2026-06-13'),
('J012','C010','RBT','Full-Time',22.00,'2026-06-14'),
('J013','C011','Behavior Therapist','Full-Time',21.00,'2026-06-15'),
('J014','C012','RBT','Full-Time',24.00,'2026-06-16'),
('J015','C013','RBT','Full-Time',25.00,'2026-06-17'),
('J016','C014','BCBA','Full-Time',46.00,'2026-06-18'),
('J017','C015','RBT','Full-Time',23.00,'2026-06-19'),
('J018','C016','Behavior Therapist','Part-Time',20.00,'2026-06-20'),
('J019','C017','RBT','Full-Time',24.50,'2026-06-21'),
('J020','C018','BCBA','Full-Time',43.00,'2026-06-22'),
('J021','C019','RBT','Full-Time',22.50,'2026-06-23'),
('J022','C020','RBT','Full-Time',23.50,'2026-06-24'),
('J023','C021','BCBA','Full-Time',45.50,'2026-06-25'),
('J024','C022','RBT','Part-Time',21.50,'2026-06-26'),
('J025','C023','RBT','Full-Time',23.50,'2026-06-27'),
('J026','C024','Behavior Therapist','Full-Time',22.50,'2026-06-28'),
('J027','C025','RBT','Full-Time',24.00,'2026-06-29'),
('J028','C026','BCBA','Full-Time',44.50,'2026-06-30'),
('J029','C027','RBT','Full-Time',22.50,'2026-07-01'),
('J030','C028','Behavior Therapist','Full-Time',21.50,'2026-07-02'),
('J031','C029','RBT','Full-Time',24.00,'2026-07-03'),
('J032','C030','BCBA','Full-Time',46.50,'2026-07-04');







