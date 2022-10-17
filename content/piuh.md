---
title: "Piuh"
date: 2021-03-30T21:37:45+09:00
draft: true
---


 ## 1. QueryDeleteCdGrp
 --- 
 ``` 
DELETE FROM IEMA_CDGRP 
WHERE 1 = ? 
 ``` 
 ## 2. QueryDeleteCode
 --- 
 ``` 
DELETE FROM IEMA_CD 
WHERE 1 = ? 
 ``` 
 ## 3. QueryInsert
 --- 
 ``` 
 INSERT INTO IPUS_CUST_INFO_USE_HIST ( 
 DUP_SCRB_CHK_INFO, SITE_CD, PSNL_INFO_OP_CD, 
 PSNL_INFO_USE_PURP_CD, PSNL_INFO_OUTINST_CD, OCCR_DTM, 
 AUDIT_ID, AUDIT_DTM, END_DTM, PSNL_INFO_OFR_ITM_CD,  
 SCND_PSNL_INFO_OUTINST_CD, PSNL_INFO_CL_CD, CO_CL_CD, 
 CS_OF_CL_CD, RS_CLM_01, RS_CLM_02, RS_CLM_03 
 ) VALUES ( 
 ?, ?, ?,  
 ?, ?, to_date(?,'YYYYMMDDHH24MISS'),  
 ?,to_date(?,'YYYYMMDDHH24MISS'), to_date(?,'YYYYMMDDHH24MISS'), ?,  
 ?, ?, ?,  
 ?, ?, ?, ? ) 
 ``` 
 ## 4. QueryInsertCdGrp
 --- 
 ``` 
INSERT INTO IEMA_CDGRP ( 
CD_GRP, NM_GRP, DESC_GRP, YN_USE, YN_UPDATE, ID_INSERT, 
DT_INSERT, ID_UPDATE, DT_UPDATE, FG_LANG 
 ) values ( 
 ?, ?, ?, 'Y', 
 'N', 'admin', sysdate, 'admin', 
 sysdate, 'KR' ) 
 ``` 
 ## 5. QueryInsertCode
 --- 
 ``` 
INSERT INTO IEMA_CD ( 
CD_GRP, NO_CD,NM_CD, DESC_CD, YN_USE, ID_INSERT, DT_INSERT, 
ID_UPDATE, DT_UPDATE, NO_ORDER, FG_LANG, USE_GOAL, USE_COMP 
)  values( 
 ?, ?, ?, ?, 
 'Y', 'admin', ?, 'admin', 
 ?,'', 'KR','','' ) 
 ``` 
 ## 6. QueryInsertDcba
 --- 
 ``` 
 INSERT INTO /*+ APPEND */ ZDCB_PSNL_INFO_USE_DTL_HST NOLOGGING (                                                  
 SEQ_NO, DUP_SCRB_CHK_INFO, SVC_CD, SVC_MGMT_NUM, SVC_NUM, CUST_NM, SITE_CD,                                       
 OP_CL_CD, OP_CL_CD_NM, CP_NM, CP_URL, AUTH_PROXY_CO_NM, AUTH_PROXY_CO_NUM,                                        
 OCCR_DTM, AUTH_YN, SVC_SCRB_DT, SVC_TERM_DT, NM_CHG_DT, AUDIT_ID, AUDIT_DTM                                       
 ) VALUES (                                                                                                        
ZDCB_PSNL_INFO_USE_DTL_HST_SEQ.nextval, ?, ?, ?, ?, ?, ?, ?, ?, ?, ?, ?, ?, to_date(?,'YYYY/MM/DD HH24:MI:SS'), ?, ?, ?, ?, ?, to_date(?,'YYYY/MM/DD HH24:MI:SS'))  
 ``` 
 ## 7. QueryInsertPams
 --- 
 ``` 
 INSERT INTO /*+ APPEND */ ZPAM_PSNL_INFO_USE_DTL_HST NOLOGGING (                                                  
 SEQ_NO, DUP_SCRB_CHK_INFO, SVC_CD, SVC_MGMT_NUM, SVC_NUM, CUST_NM, SITE_CD,                                       
 OP_CL_CD, OP_CL_CD_NM, CP_NM, CP_URL, AUTH_PROXY_CO_NM, AUTH_PROXY_CO_NUM,                                        
 OCCR_DTM, AUTH_YN, SVC_SCRB_DT, SVC_TERM_DT, NM_CHG_DT, AUDIT_ID, AUDIT_DTM                                       
 ) VALUES (                                                                                                        
ZPAM_PSNL_INFO_USE_DTL_HST_SEQ.nextval, ?, ?, ?, ?, ?, ?, ?, ?, ?, ?, ?, ?, to_date(?,'YYYY/MM/DD HH24:MI:SS'), ?, ?, ?, ?, ?, to_date(?,'YYYY/MM/DD HH24:MI:SS'))  
 ``` 
 ## 8. QueryInsertQics
 --- 
 ``` 
 INSERT INTO /*+ APPEND */ ZQIC_PSNL_INFO_USE_DTL_HST NOLOGGING (                                                  
 DUP_SCRB_CHK_INFO, SVC_MGMT_NUM, SVC_CD, SVC_NUM, CUST_NM, SITE_CD,                                       
 OP_CL_CD_NM,                                        
 OCCR_DTM, PSNL_INFO_USE_PURP_NM, OFR_TM_CTT, PSNL_INFO_OUTINST_NM, PSNL_INFO_OFR_ITM_NM, AUDIT_ID, AUDIT_DTM                                       
 ) VALUES (                                                                                                        
 ?, ?, ?, ?, ?, ?, ?, ?, ?, ?, ?, ?, ?, ?)  
 ``` 
 ## 9. QueryInsertScrbMeg
 --- 
 ``` 
 INSERT INTO IPUS_UKEY_SCRB_INFO_MEG ( 
 DUP_SCRB_CHK_INFO, SVC_CD, SVC_MGMT_NUM, 
 SVC_NUM, SVC_SCRB_DT, SVC_TERM_DT, 
 AUDIT_ID, AUDIT_DTM, CUST_NUM ,CUST_NM
 ) VALUES ( 
 ?, ?, ?,  
 ?, ?, ?,  
 ?, TO_DATE(?,'YYYY-MM-DD HH24:MI:SS'), ?,? ) 
 ``` 
 ## 10. QueryInsertScrbMeg2
 --- 
 ``` 
 INSERT INTO IPUS_UKEY_SCRB_INFO_MEG2 ( 
 DUP_SCRB_CHK_INFO, SVC_CD, SVC_MGMT_NUM, 
 SVC_NUM, SVC_SCRB_DT, SVC_TERM_DT, 
 AUDIT_ID, AUDIT_DTM, CUST_NUM ,CUST_NM
 ) VALUES ( 
 ?, ?, ?,  
 ?, ?, ?,  
 ?, TO_DATE(?,'YYYY-MM-DD HH24:MI:SS'), ?,? ) 
 ``` 
 ## 11. QueryInsertUpdateUseDtlBillBatch
 --- 
 ``` 
 INSERT INTO TMP_IPUS_INFO_USE_DTL_HST_BAT ( 
 DUP_SCRB_CHK_INFO, SVC_MGMT_NUM, PSNL_INFO_OP_CD, 
 PSNL_INFO_USE_PURP_CD, SVC_CD, PSNL_INFO_OUTINST_CD, 
 OCCR_DT, END_DT, AUDIT_ID, AUDIT_DTM, PSNL_INFO_OFR_ITM_CD, 
 SCND_PSNL_INFO_OUTINST_CD, SVC_SCRB_DT, SVC_TERM_DT, 
 SVC_NUM, CUST_NUM, PSNL_INFO_CL_CD, CO_CL_CD 
 ) VALUES ( 
 ?, ?, ?, 
 ?, ?, ?,  
 ?, ?, ?, TO_DATE(?,'YYYY-MM-DD HH24:MI:SS'), ?, 
 ?, ?, ?, 
 ?, ?, ?, ?) 
 ``` 
 ## 12. QueryInsertUseDtl
 --- 
 ``` 
 INSERT INTO IPUS_INFO_USE_DTL_HST ( 
 DUP_SCRB_CHK_INFO, SVC_MGMT_NUM, PSNL_INFO_OP_CD, 
 PSNL_INFO_USE_PURP_CD, SVC_CD, PSNL_INFO_OUTINST_CD, 
 OCCR_DT, END_DT, AUDIT_ID, AUDIT_DTM, PSNL_INFO_OFR_ITM_CD, 
 SCND_PSNL_INFO_OUTINST_CD, SVC_SCRB_DT, SVC_TERM_DT, 
 SVC_NUM, CUST_NUM, PSNL_INFO_CL_CD, CO_CL_CD 
 ) VALUES ( 
 ?, ?, ?, 
 ?, ?, ?,  
 ?, ?, ?, TO_DATE(?,'YYYY-MM-DD HH24:MI:SS'), ?, 
 ?, ?, ?, 
 ?, ?, ?, ?) 
 ``` 
 ## 13. QueryInsertUseDtlBatchMeg
 --- 
 ``` 
 INSERT INTO /*+APPEND*/ IPUS_INFO_USE_DTL_HST_MEG NOLOGGING( 
 DUP_SCRB_CHK_INFO, SVC_MGMT_NUM, PSNL_INFO_OP_CD, 
 PSNL_INFO_USE_PURP_CD, SVC_CD, PROD_ID, PSNL_INFO_OUTINST_CD, 
 OCCR_DT, END_DT, AUDIT_ID, AUDIT_DTM, PSNL_INFO_OFR_ITM_CD, 
 SCND_PSNL_INFO_OUTINST_CD, SVC_SCRB_DT, SVC_TERM_DT, 
 SVC_NUM, CUST_NUM, PSNL_INFO_CL_CD, CO_CL_CD, NM_CHG_DT 
 ) VALUES ( 
 ?, ?, ?, 
 ?, ?, ?, ?,  
 ?, ?, ?, TO_DATE(?,'YYYY-MM-DD HH24:MI:SS'), ?, 
 ?, ?, ?, 
 ?, ?, ?, ?, ?) 
 ``` 
 ## 14. QueryInsertUseDtlBatchMeg2
 --- 
 ``` 
 INSERT INTO IPUS_INFO_USE_DTL_HST_MEG2( 
 DUP_SCRB_CHK_INFO, SVC_MGMT_NUM, PSNL_INFO_OP_CD, 
 PSNL_INFO_USE_PURP_CD, SVC_CD, PROD_ID, PSNL_INFO_OUTINST_CD, 
 OCCR_DT, END_DT, AUDIT_ID, AUDIT_DTM, PSNL_INFO_OFR_ITM_CD, 
 SCND_PSNL_INFO_OUTINST_CD, SVC_SCRB_DT, SVC_TERM_DT, 
 SVC_NUM, CUST_NUM, PSNL_INFO_CL_CD, CO_CL_CD, NM_CHG_DT 
 ) VALUES ( 
 ?, ?, ?, 
 ?, ?, ?, ?,  
 ?, ?, ?, TO_DATE(?,'YYYY-MM-DD HH24:MI:SS'), ?, 
 ?, ?, ?, 
 ?, ?, ?, ?, ?) 
 ``` 
 ## 15. QueryInsertUseDtlBill
 --- 
 ``` 
 INSERT INTO IPUS_INFO_USE_DTL_HST_ljy ( 
 DUP_SCRB_CHK_INFO, SVC_MGMT_NUM, PSNL_INFO_OP_CD, 
 PSNL_INFO_USE_PURP_CD, SVC_CD, PROD_ID, PSNL_INFO_OUTINST_CD, 
 OCCR_DT, END_DT, AUDIT_ID, AUDIT_DTM, PSNL_INFO_OFR_ITM_CD, 
 SCND_PSNL_INFO_OUTINST_CD, SVC_SCRB_DT, SVC_TERM_DT, 
 SVC_NUM, CUST_NUM, PSNL_INFO_CL_CD, CO_CL_CD, NM_CHG_DT 
 ) VALUES ( 
 ?, ?, ?, 
 ?, ?, ?, ?,  
 ?, ?, ?, TO_DATE(?,'YYYY-MM-DD HH24:MI:SS'), ?, 
 ?, ?, ?, 
 ?, ?, ?, ?, ?) 
 ``` 
 ## 16. QueryInsertUseDtlTest
 --- 
 ``` 
 INSERT INTO IPUS_INFO_USE_DTL_HST_TEST( 
 DUP_SCRB_CHK_INFO, SVC_MGMT_NUM, PSNL_INFO_OP_CD, 
 PSNL_INFO_USE_PURP_CD, SVC_CD, PROD_ID, PSNL_INFO_OUTINST_CD, 
 OCCR_DT, END_DT, AUDIT_ID, AUDIT_DTM, PSNL_INFO_OFR_ITM_CD, 
 SCND_PSNL_INFO_OUTINST_CD, SVC_SCRB_DT, SVC_TERM_DT, 
 SVC_NUM, CUST_NUM, PSNL_INFO_CL_CD, CO_CL_CD, NM_CHG_DT 
 ) VALUES ( 
 ?, ?, ?, 
 ?, ?, ?, ?,  
 ?, ?, ?, TO_DATE(?,'YYYY-MM-DD HH24:MI:SS'), ?, 
 ?, ?, ?, 
 ?, ?, ?, ?, ?) 
 ``` 
 ## 17. QueryInsertUsePurp
 --- 
 ``` 
INSERT INTO IPUS_INFO_USE_PURP( 
PSNL_INFO_OP_CD,PSNL_INFO_USE_PURP_CD,PROD_ID, 
EFF_STA_DT,EFF_END_DT,AUDIT_ID,AUDIT_DTM, 
PSNL_INFO_OUTINST_CD,SCND_PSNL_INFO_OUTINST_CD, 
PSNL_INFO_OFR_ITM_CD,OFR_TM_CTT 
) VALUES ( 
 ?, ?, ?,  
 ?, ?, ?, to_date(?,'YYYY-MM-DDHH24:MI:SS'), 
 ?, ?,  
 ?, ? ) 
 ``` 
 ## 18. QuerySelect
 --- 
 ``` 
 SELECT 
 OCCR_DT,OCCR_HMS, DUP_SCRB_CHK_INFO, SITE_CD, PSNL_INFO_OP_CD, 
 PSNL_INFO_USE_PURP_CD, PSNL_INFO_OUTINST_CD, END_DT, PSNL_INFO_OFR_ITM_CD, 
 SCND_PSNL_INFO_OUTINST_CD, PSNL_INFO_CL_CD, CO_CL_CD, CS_OF_CL_CD, 
 RS_CLM_01, RS_CLM_02, RS_CLM_03, AUDIT_ID, AUDIT_DTM 
 FROM IPUS_CUST_INFO_USE_HIST 
 WHERE 1 = 1 
 ``` 
 ## 19. QueryUpdateScrb
 --- 
 ``` 
 UPDATE IPUS_UKEY_SCRB_INFO 
 SET SVC_TERM_DT = ? 
 WHERE SVC_CD = ? 
   AND SVC_MGMT_NUM = ? 
   AND SVC_SCRB_DT = ? 
   AND CUST_NUM = ? 
 ``` 
 ## 20. QueryUpdateScrbMeg
 --- 
 ``` 
  MERGE INTO /*+ parallel(M1 4) parallel(S1 4) index(S1 IPUS_UKEY_SCRB_INFO_PK) */                       
    IPUS_UKEY_SCRB_INFO S1                                                                          
    USING (SELECT  DUP_SCRB_CHK_INFO, SVC_CD, SVC_MGMT_NUM, SVC_NUM, SVC_SCRB_DT,                        
                   SVC_TERM_DT, CUST_NUM,CUST_NM, AUDIT_ID, AUDIT_DTM                                    
             FROM  IPUS_UKEY_SCRB_INFO_MEG) M1                                                           
       ON(                                                                                               
              S1.DUP_SCRB_CHK_INFO         = M1.DUP_SCRB_CHK_INFO                                       
            AND S1.SVC_MGMT_NUM              = M1.SVC_MGMT_NUM                                           
            AND S1.SVC_CD                    = M1.SVC_CD                                                 
            AND S1.SVC_SCRB_DT               = M1.SVC_SCRB_DT                                            
         )                                                                                               
             WHEN NOT MATCHED THEN                                                                       
                 INSERT( S1.DUP_SCRB_CHK_INFO, S1.SVC_CD, S1.SVC_MGMT_NUM, S1.SVC_NUM, S1.SVC_SCRB_DT,   
                         S1.SVC_TERM_DT, S1.CUST_NUM, S1.CUST_NM, S1.AUDIT_ID, S1.AUDIT_DTM)             
                 VALUES( M1.DUP_SCRB_CHK_INFO, M1.SVC_CD, M1.SVC_MGMT_NUM, M1.SVC_NUM, M1.SVC_SCRB_DT,   
                         M1.SVC_TERM_DT, M1.CUST_NUM, M1.CUST_NM, M1.AUDIT_ID, M1.AUDIT_DTM)             
            WHEN MATCHED THEN                                                                            
                 UPDATE SET S1.SVC_TERM_DT = M1.SVC_TERM_DT, S1.AUDIT_DTM = M1.AUDIT_DTM                 
 ``` 
 ## 21. QueryUpdateScrbMeg2
 --- 
 ``` 
MERGE /*+PARALLEL(A 4) PARALLEL(B 4) */ INTO IPUS_UKEY_SCRB_INFO A                 
      USING (SELECT SVC_CD, SVC_MGMT_NUM, SVC_SCRB_DT, CUST_NUM, SVC_TERM_DT       
                    FROM IPUS_UKEY_SCRB_INFO_MEG2 WHERE SVC_TERM_DT IS NOT NULL) B 
                    ON(                                                            
                              A.SVC_CD = B.SVC_CD                                  
                          AND A.SVC_MGMT_NUM = B.SVC_MGMT_NUM                      
                          AND A.SVC_SCRB_DT = B.SVC_SCRB_DT                        
                          AND A.CUST_NUM = B.CUST_NUM                              
                      )                                                            
      WHEN MATCHED THEN                                                            
            UPDATE SET A.SVC_TERM_DT = B.SVC_TERM_DT                               
 ``` 
 ## 22. QueryUpdateUseDtl
 --- 
 ``` 
UPDATE IPUS_INFO_USE_DTL_HST 
SET SVC_TERM_DT = ?, 
    END_DT = ?, 
    AUDIT_DTM = TO_DATE(?,'YYYY-MM-DD HH24:MI:SS') 
WHERE DUP_SCRB_CHK_INFO = ? 
  AND SVC_MGMT_NUM = ? 
  AND PSNL_INFO_OP_CD = DECODE( ?,'A002','A001','A004','A003','A006','A005','A008','A007',?) 
  AND PSNL_INFO_USE_PURP_CD = ? 
  AND SVC_CD = ? 
  AND PSNL_INFO_OUTINST_CD = ? 
  AND OCCR_DT = ? 
  AND AUDIT_ID = ? 
  AND PSNL_INFO_OFR_ITM_CD = ? 
  AND CO_CL_CD = ? 
 ``` 
 ## 23. QueryUpdateUseDtlBatch
 --- 
 ``` 
UPDATE IPUS_INFO_USE_DTL_HST 
SET SVC_TERM_DT = ?, 
    END_DT = ? 
  WHERE SVC_MGMT_NUM = ? 
  AND PSNL_INFO_OP_CD = DECODE( ?,'A002','A001','A004','A003','A006','A005','A008','A007',?) 
  AND SVC_CD = ? 
  AND PROD_ID = ? 
  AND OCCR_DT = ? 
 ``` 
 ## 24. QueryUpdateUseDtlBatchMeg
 --- 
 ``` 
MERGE INTO /*+ parallel(M1 4) parallel(H1 4) index(H1 IPUS_INFO_USE_DTL_HST_PK) */                               
IPUS_INFO_USE_DTL_HST H1                                                                                         
    USING (SELECT  DUP_SCRB_CHK_INFO, SVC_MGMT_NUM, PSNL_INFO_OP_CD, PSNL_INFO_USE_PURP_CD,                      
                   SVC_CD, PROD_ID, PSNL_INFO_OUTINST_CD, OCCR_DT, END_DT, AUDIT_ID,                             
                   AUDIT_DTM, PSNL_INFO_OFR_ITM_CD, SCND_PSNL_INFO_OUTINST_CD, SVC_SCRB_DT,                      
                   SVC_TERM_DT,SVC_NUM, CUST_NUM, PSNL_INFO_CL_CD, CO_CL_CD, NM_CHG_DT                           
             FROM  IPUS_INFO_USE_DTL_HST_MEG) M1                                                                 
       ON(                                                                                                       
              H1.DUP_SCRB_CHK_INFO         = M1.DUP_SCRB_CHK_INFO                                              
            AND H1.SVC_MGMT_NUM              = M1.SVC_MGMT_NUM                                                   
            AND H1.PSNL_INFO_OP_CD           = M1.PSNL_INFO_OP_CD                                                
            AND H1.PSNL_INFO_USE_PURP_CD     = M1.PSNL_INFO_USE_PURP_CD                                          
            AND H1.SVC_CD                    = M1.SVC_CD                                                         
            AND H1.PROD_ID                   = M1.PROD_ID                                                        
            AND H1.PSNL_INFO_OUTINST_CD      = M1.PSNL_INFO_OUTINST_CD                                           
            AND H1.OCCR_DT                   = M1.OCCR_DT                                                        
         )                                                                                                       
             WHEN MATCHED THEN                                                                                   
              UPDATE                                                                                          
                  SET H1.NM_CHG_DT = M1.NM_CHG_DT, H1.AUDIT_DTM = M1.AUDIT_DTM                                
             WHEN NOT MATCHED THEN                                                                               
                 INSERT(H1.DUP_SCRB_CHK_INFO, H1.SVC_MGMT_NUM, H1.PSNL_INFO_OP_CD, H1.PSNL_INFO_USE_PURP_CD,     
                        H1.SVC_CD, H1.PROD_ID, H1.PSNL_INFO_OUTINST_CD, H1.OCCR_DT, H1.END_DT, H1.AUDIT_ID,      
                        H1.AUDIT_DTM, H1.PSNL_INFO_OFR_ITM_CD, H1.SCND_PSNL_INFO_OUTINST_CD, H1.SVC_SCRB_DT,     
                        H1.SVC_TERM_DT, H1.SVC_NUM, H1.CUST_NUM, H1.PSNL_INFO_CL_CD, H1.CO_CL_CD, H1.NM_CHG_DT)  
                 VALUES(M1.DUP_SCRB_CHK_INFO, M1.SVC_MGMT_NUM, M1.PSNL_INFO_OP_CD, M1.PSNL_INFO_USE_PURP_CD,     
                        M1.SVC_CD, M1.PROD_ID, M1.PSNL_INFO_OUTINST_CD, M1.OCCR_DT, M1.END_DT, M1.AUDIT_ID,      
                        M1.AUDIT_DTM, M1.PSNL_INFO_OFR_ITM_CD, M1.SCND_PSNL_INFO_OUTINST_CD, M1.SVC_SCRB_DT,     
                        M1.SVC_TERM_DT, M1.SVC_NUM, M1.CUST_NUM, M1.PSNL_INFO_CL_CD, M1.CO_CL_CD, M1.NM_CHG_DT)  
 ``` 
 ## 25. QueryUpdateUseDtlBatchMeg2
 --- 
 ``` 
MERGE /*+ PARALLEL(M1 4) PARALLEL(H1 4) USE_NL(M1 H1) */                                                                                           
      INTO IPUS_INFO_USE_DTL_HST H1                                                                                                                
      USING (SELECT SVC_CD, SVC_MGMT_NUM, PROD_ID, PSNL_INFO_OP_CD, OCCR_DT, SVC_TERM_DT, END_DT                                                   
                    FROM IPUS_INFO_USE_DTL_HST_MEG2 WHERE SVC_TERM_DT IS NOT NULL OR END_DT IS NOT NULL) M1                                         
                 ON(                                                                                                                               
                        H1.SVC_MGMT_NUM = M1.SVC_MGMT_NUM                                                                                          
                    AND H1.PSNL_INFO_OP_CD=DECODE( M1.PSNL_INFO_OP_CD,'A002','A001','A004','A003','A006','A005','A008','A007',M1.PSNL_INFO_OP_CD)  
                    AND H1.SVC_CD = M1.SVC_CD                                                                                                      
                    AND H1.PROD_ID = M1.PROD_ID                                                                                                    
                    AND H1.OCCR_DT = M1.OCCR_DT )                                                                                                  
      WHEN MATCHED THEN                                                                                                                            
            UPDATE SET H1.SVC_TERM_DT = M1.SVC_TERM_DT, H1.END_DT = M1.END_DT                                                                    
 ``` 

 
