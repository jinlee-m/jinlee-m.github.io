---
title: "π€ CRF to SDTM"
description: "λ°μ΄ν° μμ§κ³Ό λ³ν"
date: 2023-01-18
update: 2023-01-18
tags:
  - CDISC
  - CRF
  - SDTM
series: "CDISC μμλ³΄κΈ°"
---

# CRF μ€ν <a name="CRF_Renditions"/>
style-sheetκ° ODM-xml λ¬Έμμμ λΈλΌμ°μ μ CRF νμ΄μ§λ₯Ό μμ±νλ λ°©λ²μ λν κ°λ¨ν μ€λͺμλλ€.

## CRF layout <a name="CRF_layout"/>
μ¬κΈ°μ μ μλ CRF λ μ΄μμμ μ£Όμ κΈ°λ₯μ κ° μ§λ¬Έ λΌμΈμ μΈμ ν μ΄μ SDTM μ£Όμμ λ°°μΉνλ κ²μλλ€.
μ΄λ κ² νλ©΄ μ£Όμ μμλ₯Ό CRF μμμ λ΄λΆμ μλ¨μΌλ‘ μ΄λν  νμ μμ΄ SDTM μ£Όμμ΄ μ μ ν μμΉμ νμλ©λλ€.
μ΄κ²μ΄ CRF μμ λλΉμμ μ½κ°μ κ³΅κ°μ μ°¨μ§νλλΌλ
[acrf](/examples/acrf.pdf)λ SDTM μ£Όμμ λ¬Έμμ΄κ³  [bcrf](/examples/bcrf.pdf)λ CRF νμ΄μ§ μμ²΄μ λ¬Έμμλλ€.
μ΄ λΆν μ λν λ³΄λ€ νλΆν SDTM μ£Όμμ μν κ³΅κ°μ νμ©ν©λλ€.

![Example CRF rendition from pure ODM-xml](images/CRF.png)

CRF λ³νμ **FormDef** νκ·Έλ‘ μλ³λλ CRFμ κ° μμμ λν νλμ νμ΄λΈλ‘ κ΅¬μ±λλ©° μλ μ΄μ΄ μμ΅λλ€.

1. ODM-xml νμΌμ μλ **ItemGroupRef** λ° **ItemRef** νκ·Έμ **@OrderNumber** μμ±μμ κ΅¬μ±λ μνμ€ λ²νΈμλλ€. μ΄ λ²νΈλ CRF μ½νμΈ λ₯Ό λΌμνκ³  κ²ν ν  λ μ¬λμ΄ μ°Έμ‘°νλ μ­ν μ ν  λΏλ§ μλλΌ CRF μμμ μ λ ¬μ μΆμ ν©λλ€. μμ λλ μ§λ¬Έμ κ΅¬ν μ°Έκ³  μ¬ν­μ΄ μλ κ²½μ° λ²νΈ μμ ν΄μ κΈ°νΈ(**#**)κ° νμλκ³  μ€μ  μ°Έκ³  μ¬ν­μ CRF νμ΄μ§ λ€ κ°μ£Όμ λ²νΈλ₯Ό μ°Έμ‘°νμ¬ νμλ©λλ€.
2. **Question/TranslatedText** νκ·Έλ‘ μλ³λ CRF μμμ μ§λ¬Έμλλ€. **Alias[@Context='completionInstructions']/@Name** νκ·Έμ λͺ¨λ  μλ£ μ§μΉ¨μ μ§λ¬Έκ³Ό ν¨κ» νμλ©λλ€.
3. **@DataType** μμ±μΌλ‘ κ΅¬λΆλλ μ§λ¬Έμ λν λ΅λ³μλλ€. κ° λ°μ΄ν° μ νμ ν΄λΉ μ νμ HTML νκ·Έμ λν λΈλΌμ°μ λ³ ν΄μμΌλ‘ νμλ©λλ€. λ€μ€ μ νμ λν νμκ° ODM μ μμ μ‘΄μ¬νμ§ μκΈ° λλ¬Έμ μ΄ λ°μ΄ν° μ νμ νκ·Έ λ΄μμ **μ μ©λλ λͺ¨λ (all that apply)** λ¬Έμμ΄μ μν΄ νΈλ¦¬κ±°λλ νμ€νΈ μμ²΄μμ μΆμΆλ©λλ€.
   * ItemDef/@Name
   * ItemDef/Question/TranslatedText
   * ItemDef/Description/TranslatedText
   * ItemDef/Alias[@Context='completionInstructions']/@Name
4. **@SDSVarName** μμ±μΌλ‘ μλ³λλ SDTM μ£Όμμλλ€. SDTM μ£Όμ λ§μ»€λ‘ **@Context='SDTM'** μμ±μ κ°λ **Alias/@Name** μμ±μμ μΆκ° μ λ³΄κ° μΆκ°λ©λλ€. κ° λ¬Έμ₯μ `'. '`λ‘ κ΅¬λΆλ©λλ€. SDTM μ£Όμμ '(λ§μΉ¨ν κ³΅λ°±)μ κ°λμ±μ μν΄ μμ²΄ νμ νμλ©λλ€. SDTM λ°μ΄ν° μΈνΈ μ΄λ¦μ **ItemGroupDef/@Domain** λλ **ItemDef/@SDSVarName** μμ±μμ μΆμΆλ©λλ€. μ¬κΈ°μ νμλ λ§μΉ¨ν `dataset.variable`λ‘ κ΅¬λΆλ 2λ¨κ³ μ΄λ¦μΌ μ μμ΅λλ€.

## Design choices <a name="Design_choices"/>
ODM-XML νμΌμ λν λͺ¨λ  κ³΅κΈμμ²΄λ³ μ΄λ¦ κ³΅κ° λ° XML λΆλ‘μ λ¬΄μλ©λλ€.

ODM-XML νμΌ XPATHμ νΉμ±κ³Ό κ΄λ ¨νμ¬ λ€μκ³Ό κ°μ κ°μ μ΄ μ¬μ©λ©λλ€.:

CRF Element             | XPath                                                          | Comment
---                     | ---                                                            | ---
Form Title/Name         | FormDef/Description/TranslatedText                             | As it appears on the CRF<br/>
Section Title/Name      | Sections/ItemGroup/@Name                                       | Never displayed
Question Text           | ItemDef/Question/TranslatedText                                | As it appears on the CRF
Prompt                  | ItemDef/Alias[@Context="prompt"]/@Name                         | If present in ODM-XML
Completion Instructions | ItemDef/Alias[@Context="completionInstructions"]/@Name         | If present in ODM-XML
Implementation Notes    | ItemDef/Alias[@Context="implementationNotes"]/@Name            | If present in ODM-XML
Mapping Instructions    | ItemDef/Alias[@Context='mappingInstructions']/@Name            | If present in ODM-XML
CDASH                   | ItemDef/Alias[@Context="CDASH"]/@Name                          | Optional, controlled by a parameter
SDTM                    | ItemDef/@SDSVarName <br/> ItemDef/Alias[@Context="SDTM"]/@Name | When @Domain attribute not present, Dataset.Variable syntax is assumed

CRF μ½νμΈ λΏλ§ μλλΌ ν° μκ°μ [eCRF portal on the CDISC website](https://www.cdisc.org/kb/ecrf)μμ κ°μ Έμ΅λλ€. λ΄ μλ£¨μμ μ μ©νκΈ° μν΄ CRF μ½νμΈ λ₯Ό κ±°μ λ³κ²½νμ§ μμμ΅λλ€. μ¬κΈ°μλ λ€μκ³Ό κ°μ SDTM μ£Όμ λ° μ ν ν­λͺ© μ λ¦¬κ° ν¬ν¨λ©λλ€. μλ₯Ό λ€μ΄,
* λͺ¨λ  νμ€νΈ μμλ λ°μ΄νλ‘ λ¬Άμ¬ μμ΅λλ€.
* SDTM μ£Όμμμ μμλ°μ΄νλ₯Ό μΌκ΄λκ² μ¬μ©
* κ° CRF μ§λ¬Έμ λν μ°Έμ‘° λ²νΈ μΆκ°. μ΄λ CRFλ₯Ό κ²ν ν  λ μ μ©ν κ²μΌλ‘ μμ¦λμμ΅λλ€.
* μ§μΉ¨/λ©λͺ¨λ λ μμ κΈκΌ΄κ³Ό μ΄ν€λ¦­μ²΄(_italics_)λ‘ μμ±λ©λλ€.

### SDTM Datasets and Variables <a name="SDTM_Datasets_and_Variables"/>
ODM-XMLμμ SDTM μ£Όμμ λν λ°μ΄ν° μΈνΈ μ΄λ¦ λ° λ³μ μ΄λ¦μ μΊ‘μ²νλ λ°©λ²μ λν΄ μΌλΆ λΌμμ΄ μμμ΅λλ€. μΌλΆ ODM νΈμ§/μμ± μμ€νμ **ItemGroupDef/@Domain** μμ±μ μ¬μ©νμ¬ λ°μ΄ν° μΈνΈ μ΄λ¦μ λ³΄μ νκ³  μΌλΆλ κ·Έλ μ§ μμ΅λλ€. λλΆλΆμ SDTM λ³μ μ΄λ¦μ λν **ItemDef/@SDSVarName**μ λμνλ κ² κ°μ΅λλ€. λ λ€ μ§μνκΈ°λ‘ μ ννμ΅λλ€. μ΄λ **ItemGroupDef/@Domain**μ μ ννμ§λ§ **ItemDef/@SDSVarName**μμ 2λ¨κ³ μ΄λ¦μ μ¬μ©νλ κ²μ΄ μ’μ΅λλ€.

μ΄μ λν μ£Όλ μ΄μ λ **@ItemGroupDef** μμ€μ **@Domain** μμ±μ μλ λ°μ΄ν° μΈνΈ μ΄λ¦κ³Ό **ItemDef** μμ€μ **SDSVarName** μμ±μ μλ λ³μ μ΄λ¦μ κ°μ§μΌλ‘μ¨ λΆκ³Όλλ CRF λ μ΄μμκ³Ό SDTM μ£Όμ μ¬μ΄μ λ°μΈλ©μ μ κ±°νκΈ° λλ¬Έμλλ€.νμ΄λΈ νμμ λ°μ΄ν° μΈνΈ/λ³μ κ΅¬μ‘°λ₯Ό λͺ¨λ°©νμ¬ λΌλ¦¬μ μΌλ‘ λ³΄μΌ μ μμ§λ§ μ€μ λ‘λ CRF μμμ΄ SDTM λ°μ΄ν° μΈνΈ κ΅¬μ‘°μ λ°λΌ μ€κ³λμ΄μΌ νλ€λ μ§μ μΈμλ μλ¬΄λ° λͺ©μ μ΄ μμ΅λλ€.μ€μ  κ²½νμ λ°λ₯΄λ©΄ λ³΅μ‘ν μμ(μ: Adverse events)μ μ’μ’ μλ‘ λ€λ₯Έ SDTM λλ©μΈ(μ: AE λ° SUPPAE)μ λ²κ°μ μ£Όμμ λ¬κ³  λ°λΌμ **@ItemGroupDef** (sections)λ₯Ό λ³κ²½νμ¬ λλ©μΈμ λ³κ²½νλλ‘ μ§μνκ³  SDTM μ£Όμ λͺ©μ λ§ μ κ³΅ν©λλ€.

λ΄ [interim] μλ£¨μμ **SDSVarName**μ κ³΅ν΅ SQL μ€νμΌμ λ§μΉ¨ν(μ: AE.AETERM)λ‘ κ΅¬λΆλ λ°μ΄ν° μΈνΈ μ΄λ¦κ³Ό λ³μ μ΄λ¦μ λͺ¨λ ν¬ν¨νλλ‘ νλ κ²μλλ€. λ³΄λ€ μ°μνκ³  μκ΅¬μ μΈ μλ£¨μμ [CDISC](https://www.cdisc.org/)κ° **@Domain** μμ±μ ODM-XML μ¬μμ **ItemDef** λ λ²¨λ‘ μ΄λνλλ‘ μΉνΈνλ κ²μλλ€. μ΄λ κ² νλ©΄ λ°μ΄ν° μΈνΈ μ΄λ¦μ΄ λ³μ μ΄λ¦κ³Ό λμΌν μμ€μμ μ§μ λμ΄ SDTM μ£Όμ λ€μμ CRF μΉμμ κ΅¬μ±ν  νμκ° μμ΅λλ€. μ΄κ²μ ODM νμΌμμ λ°μ΄ν° μΈνΈ μ΄λ¦μ μ€λ³΅ μ¬μμ μκ΅¬νμ§λ§ ODM νΈμ§/μμ± μμ€νμ SDTM μ¬μμμ μ΄λ₯Ό μ±μΈ μ μμ΄μΌ ν©λλ€.


## Parameters <a name="Parameters"/>
Parameters to the `crf_1_3_2.xsl` file are documented in the table below

Parameter | Description | Default value | Comment
---         | ---                                 | ---                        | ---
parmdisplay | Display mode                        | spec                       | **spec**: CRF specification with implementation notes, SDTM annotations, etc. <br/> **bcrf**: Blank CRF for submission <br/> **acrf**: SDTM annotated CRF for submission <br/> **book**: Complete CRF book with forms repeated by visit
parmstudy   | Name of study or standard           |                            | Can be derived from ODM file name
parmversion | Version of the ODM-XML file         |                            | Can be derived from ODM file name
parmstatus  | Status of the ODM-XML file          |                            | Can be derived from ODM file name
parmname    | Company name                        | My Company                 | User supplied
parmlogo    | Company logo file name              |                            | User supplied
parmlang    | Language of TranslatedText          | All, assuming one language | Future implementation
parmcdash   | Display CDASH annotation from Alias | 1                          | If present, 0 or 1

## Creating PDF documents <a name="Creating_PDF_documents"/>
λͺ¨λ  λΈλΌμ°μ μμ SDTM μ£Όμμ΄ λ¬λ¦° CRF μ¬μ, μμ ν CRF book, [acrf](/examples/acrf.pdf) or [bcrf](/examples/bcrf.pdf) μ μΆ λ¬Έμλ‘ κ°κ° λμ€ν¬μ PDF λ¬Έμλ‘ CRF λ³νμ μΈμν©λλ€.
μ°Έκ³ :
* μ¨μ€ν¬λ¦° λ²νΌμ PDF νμΌλ‘ μΈμνμ¬ μμ±λ PDF λ¬Έμμλ ν¬ν¨λμ§ μμ΅λλ€.
* TOCλ PDF λ¬Έμ λ΄μ λ§ν¬λ‘ μ¬λ°λ₯΄κ² μλν©λλ€.
* λ°©λ¬Έ λ§€νΈλ¦­μ€μ μμ μ΄λ¦μ TOC μΈμ λ§ν¬λ‘λ μλν©λλ€(μλ κ²½μ°).
* SDTM μ£Όμμ λͺ¨λ  κ³΅λ°±μΌλ‘ κ΅¬λΆλ λ¨μ΄μλ **define.xml**μ CRF μΆμ²κ° νμ΄μ§ λ²νΈκ° μλ SDTM λ³μμ λν λͺλͺλ λμμΌλ‘ μμ±λ κ²½μ° **define-xml**μμ μ°κ²°ν  μ μλ λ§ν¬ λμμ΄ μμ΅λλ€.
* SDTM μ£Όμμ λΈλμ λ°°κ²½μμ μ¬μ©νλ €λ©΄ λ°°κ²½ κ·Έλν½μ PDF λ¬Έμμ μΌλΆλ‘ μΈμν΄μΌ ν©λλ€.
* λ¨Έλ¦¬κΈ λ° λ°λ₯κΈ, μΈλ‘ λ κ°λ‘ λ° κΈ°ν λ¬Έμ μμ±μ λΈλΌμ°μ μ μΈμ λν μμ λ΄μμ μ μ΄ν  μ μμ΅λλ€.
* λ€λ₯Έ λΈλΌμ°μ λ μ½κ° λ€λ₯΄κ² λμν  μ μμ΅λλ€.