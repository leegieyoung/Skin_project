# Skin_project
Step1. GWAS
/ichrogene/project/temp/gylee/Code/Association_code_folder/Article/
Step2.
/ichrogene/project/temp/gylee/0.GWAS/4.PRS/cnu/1.clinical/code.R
dosage에 사용할 vcf를 만들기 위해 필요한 샘플리스트(이후 validation.list로 변경됨)
addPheno에 사용하기 위한 임상정보

Step3. Rare variant 정리
/ichrogene/project/temp/gylee/0.GWAS/4.PRS/cnu/Train10Vali0/rare.variant.sh
 Step1. GWAS에서 SB(set-based.txt)에서 발견된 Burden or SKAT test 5e-4 를 갖는 마커 선별(melanin만 1e-4)
 wrinkle 에서는 발견되지 않음

Step4.
/ichrogene/project/temp/gylee/0.GWAS/4.PRS/cnu/Train10Vali0/sagging/onestep.AI.king3554.mac20.sh

1) PRSice2기반 clumping
bash /ichrogene/project/temp/gylee/0.GWAS/5.METAL/ct.cnu.241129.king3554.mac20.sh ${Pheno} Train10Vali0 ${cutoff} ${LD}
2) absbeta 생성
Rscript /ichrogene/project/temp/gylee/0.GWAS/Code/R/make_marker_forSAIGE.R
3) dosage기반 addPheno 생성
bash /ichrogene/project/temp/gylee/0.GWAS/4.PRS/cnu//calculate_PRS.241128.cnu_forTrain_continuous.ct.LD.king3554.mac20.Vali_king3554.sh ${Pheno} ${Pheno} ${cutoff} ${LD} Train10Vali0
위 3가지 스텝을 처리할 수 있는 코드
        치명적인 오류 발견(250303)
        Rscript /ichrogene/project/temp/gylee/0.GWAS/4.PRS/Trait_PRS_addPheno_continuous.R
        match없이 Case_ids.txt와 addPheno.csv를 결합했었음. match함수를 활용하여 코드 수정 후 R2 0.4 -> 0.9로 상승

Step5.
/ichrogene/project/temp/gylee/0.GWAS/4.PRS/cnu/ChangeDir.melanin.scale.250303.R
R2 RMSE MAE 값을 계산하는 코드(10-fold cross validation 및 holdout(0.75:0.25) 기반
