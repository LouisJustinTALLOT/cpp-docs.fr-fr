---
title: Grammaire BNF de Microsoft Macro Assembler
description: Description BNF de MASM pour x64.
ms.date: 12/17/2019
helpviewer_keywords:
- MASM (Microsoft Macro Assembler), BNF reference
ms.openlocfilehash: 29eae0b110f99f1f417e153f18aa2ac3aff5c69b
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/20/2019
ms.locfileid: "75322805"
---
# <a name="microsoft-macro-assembler-bnf-grammar"></a>Grammaire BNF de Microsoft Macro Assembler

Cette page contient une description BNF de la syntaxe MASM. Il est fourni en complément des rubriques de référence et n’est pas forcément complet. Consultez les rubriques de référence pour obtenir des informations complètes sur les mots clés, les paramètres, les opérations, etc.

Pour illustrer l’utilisation de la BNF, le diagramme suivant illustre la définition de la directive TYPEDEF, en commençant par le *typedefDir*non terminal.

![Exemple MASM BNF](media/bnf.png)

Les entrées sous chaque accolade horizontale sont des terminaux (tels que **NEAR16**, **NEAR32**, **FAR16**et **FAR32**) ou des non terminaux (tels que *qualificateur*, *qualifiedType*, *distance*et *protoSpec*) qui peuvent être définis plus en détail. Chaque non terminal en italique dans la définition de *typedefDir* est également une entrée de la BNF. Trois points verticaux indiquent une définition de branche pour un non terminal qui, par souci de simplicité, n’illustre pas cette illustration.

La grammaire BNF autorise les définitions récursives. Par exemple, la grammaire utilise qualifiedType comme définition possible pour qualifiedType, qui est également un composant de la définition du qualificateur. Le symbole « | » spécifie un choix entre d’autres expressions, par exemple *endOfLine* | *Commentaire*. Les doubles accolades spécifient un paramètre facultatif, par exemple ⟦ *macroParmList* ⟧. Les crochets n’apparaissent pas réellement dans le code source.

## <a name="masm-nonterminals"></a>Non-Terminals MASM

*;;* \
&nbsp;&nbsp;&nbsp;&nbsp;*endOfLine* | 

*= Dir*\
&nbsp;&nbsp;&nbsp;&nbsp;*id* = *immExpr* ;;

*addOp*\
&nbsp;&nbsp;&nbsp;&nbsp;+ | -

*aExpr*\
&nbsp;&nbsp;&nbsp;terme *&nbsp;*  | *aExpr*

*altId*\
&nbsp;&nbsp;&nbsp;*ID* de &nbsp;

*arbitraryText*\
&nbsp;&nbsp;&nbsp;&nbsp;*listecar*

*asmInstruction*\
&nbsp;&nbsp;&nbsp;&nbsp;*mnémonique* ⟦ *exprList* ⟧

*assumeDir*\
&nbsp;&nbsp;&nbsp;&nbsp;**Supposons** *assumeList* ;; \
&nbsp;&nbsp;&nbsp;&nbsp;| **Supposons rien** ;;

*assumeList*\
&nbsp;&nbsp;&nbsp;&nbsp;*assumeRegister* | *assumeList* , *assumeRegister*\

*assumeReg*\
&nbsp;&nbsp;&nbsp;&nbsp;*Register* : *assumeVal*

*assumeRegister*\
&nbsp;&nbsp;&nbsp;&nbsp;*assumeSegReg* | *assumeReg*

*assumeSegReg*\
&nbsp;&nbsp;&nbsp;&nbsp;*segmentRegister* : *assumeSegVal*

*assumeSegVal*\
&nbsp;&nbsp;&nbsp;&nbsp;*frameExpr* | **Nothing** | 

*assumeVal*\
&nbsp;&nbsp;&nbsp;&nbsp;*qualifiedType* | **Nothing** | 

*bcdConst*\
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *Sign* ⟧ *decNumber*

*binaryOp*\
&nbsp;&nbsp;&nbsp;&nbsp;= = | ! = | > = | < = | > | < | &

*bitDef*\
&nbsp;&nbsp;&nbsp;&nbsp;*bitFieldId* : *BitFieldSize* ⟦ = *constExpr* ⟧

*bitDefList*\
&nbsp;&nbsp;&nbsp;&nbsp;*bitDef* | *bitDefList* , ⟦;; ⟧ *bitDef*

*bitFieldId*\
&nbsp;&nbsp;&nbsp;*ID* de &nbsp;

*bitFieldSize*\
&nbsp;&nbsp;&nbsp;&nbsp;*constExpr*

*blockStatements*\
&nbsp;&nbsp;&nbsp;&nbsp;*directiveList*\
&nbsp;&nbsp;&nbsp;&nbsp;|  **. Continuez** **. Si** *cExpr* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;|  **. ARRÊTER** ⟦ **. Si** *cExpr* ⟧

*bool*\
&nbsp;&nbsp;&nbsp;&nbsp;**TRUE** | **false**

*byteRegister*\
&nbsp;&nbsp;&nbsp;&nbsp;AL | AH | CL | CH | DL | DH | BL | BH | R8B | R9B | R10B | R11B | R12B | R13B | R14B | R15B

*cExpr*\
&nbsp;&nbsp;&nbsp;&nbsp;*aExpr* | *cExpr* || *aExpr*

\ de *caractères*
&nbsp;&nbsp;&nbsp;&nbsp;tout caractère avec un nombre ordinal compris entre 0 et 255, à l’exception du saut de ligne (10).

\ *charList*
&nbsp;&nbsp;&nbsp;*caractère* &nbsp; | caractère *charList*

*className*\
&nbsp;&nbsp;&nbsp;*chaîne* de &nbsp;

*commDecl*\
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *Nearfar* ⟧ ⟦ *langType* ⟧ *ID* : *commType*\
&nbsp;&nbsp;&nbsp;&nbsp;⟦ : *constExpr* ⟧

*commDir*\
&nbsp;&nbsp;&nbsp;&nbsp;**COMM**\
&nbsp;&nbsp;&nbsp;&nbsp;*commList* ;;

\ de *Commentaires*
&nbsp;&nbsp;&nbsp;&nbsp;; *texte* ;;

*commentDir*\
&nbsp;&nbsp;&nbsp;*délimiteur* de **Commentaire** &nbsp;\
&nbsp;&nbsp;&nbsp;*texte* &nbsp;\
&nbsp;&nbsp;&nbsp;&nbsp;*texte* de *délimiteur* de *texte* ;;

*commList*\
&nbsp;&nbsp;&nbsp;&nbsp;*commDecl* | *commList* , *commDecl*

*commType*\
&nbsp;&nbsp;&nbsp;*type* de &nbsp; | *constExpr*

\ *constante*
&nbsp;&nbsp;&nbsp;&nbsp;*chiffres* ⟦ *radixOverride* ⟧

*constExpr*\
&nbsp;&nbsp;&nbsp;&nbsp;*expr*

*contextDir*\
&nbsp;&nbsp;&nbsp;&nbsp;**PUSHCONTEXT** *contextItemList* ;; \
&nbsp;&nbsp;&nbsp;&nbsp;**POPCONTEXT** *contextItemList* ;;

*contextItem*\
&nbsp;&nbsp;&nbsp;&nbsp;**suppose** |  | la **liste** ** | de** l' **UC** | **tout**

*contextItemList*\
&nbsp;&nbsp;&nbsp;&nbsp;*contextItem* | *contextItemList* , *contextItem*

*controlBlock*\
&nbsp;&nbsp;&nbsp;&nbsp;*whileBlock* | *repeatBlock*

*controlDir*\
&nbsp;&nbsp;&nbsp;&nbsp;*controlIf* | *controlBlock*

*controlElseif*\
&nbsp;&nbsp;&nbsp;&nbsp; **. ELSEIF** &nbsp;&nbsp;&nbsp;&nbsp;*cExpr* ;; \
&nbsp;&nbsp;&nbsp;&nbsp;*directiveList* \
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *controlElseif* ⟧

*controlIf*\
&nbsp;&nbsp;&nbsp;&nbsp; **. Si** &nbsp;&nbsp;&nbsp;&nbsp;*cExpr* ;; \
&nbsp;&nbsp;&nbsp;&nbsp;*directiveList*\
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *controlElseif* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;⟦ **. SINON** ;; \
&nbsp;&nbsp;&nbsp;&nbsp;[*directiveList*⟧ \
&nbsp;&nbsp;&nbsp;&nbsp; **. ENDIF** ;;

\ du *coprocesseur*
&nbsp;&nbsp;&nbsp;&nbsp;. 8087 |. 287 |. 387 |. NO87

*crefDir*\
&nbsp;&nbsp;&nbsp;&nbsp;*crefOption* ;;

*crefOption*\
&nbsp;&nbsp;&nbsp;&nbsp; **.\ CREF**
&nbsp;&nbsp;&nbsp;&nbsp;|  **. XCREF** ⟦ *idList* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;|  **. NOCREF** ⟦ *idList* ⟧

*cxzExpr*\
&nbsp;&nbsp;&nbsp;&nbsp;*expr*\
&nbsp;&nbsp;&nbsp;&nbsp;| ! *expr*\
&nbsp;&nbsp;&nbsp;&nbsp;| *expr* = = expr \
&nbsp;&nbsp;&nbsp;&nbsp;| *expr* ! = expr

*dataDecl*\
&nbsp;&nbsp;&nbsp;&nbsp;DB | DW | JJ | DF | DQ | DT | *type de données* | *typeid*

*dataDir*\
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *ID* ⟧ *DataItem* ;;

*dataItem*\
&nbsp;&nbsp;&nbsp;&nbsp;*dataDecl* *scalarInstList*\
&nbsp;&nbsp;&nbsp;&nbsp;| *structTag* *structInstList*\
&nbsp;&nbsp;&nbsp;&nbsp;| *typeid* *structInstList*\
&nbsp;&nbsp;&nbsp;&nbsp;| *unionTag* *structInstList*\
&nbsp;&nbsp;&nbsp;&nbsp;| *recordTag* *recordInstList*

*type de données*\
&nbsp;&nbsp;&nbsp;&nbsp;octet | SBYTE | MOT | ÉPÉE | DWORD | SDWORD | FWORD | QWORD | SQWORD | TO | OWORD | REAL4 | REAL8 | REAL10 | MMWORD | XMMWORD | YMMWORD

*decdigit*\
&nbsp;&nbsp;&nbsp;&nbsp;0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 0,9

*decNumber*\
&nbsp;&nbsp;&nbsp;&nbsp;*decdigit*\
&nbsp;&nbsp;&nbsp;&nbsp;| *decNumber* *decdigit*

*délimiteur*\
&nbsp;&nbsp;&nbsp;&nbsp;n’importe quel caractère, à l’exception de *whiteSpaceCharacter*

*chiffres*\
&nbsp;&nbsp;&nbsp;&nbsp;*decdigit*\
&nbsp;&nbsp;&nbsp;&nbsp;| *chiffres* *decdigit*\
&nbsp;&nbsp;&nbsp;&nbsp;| *chiffres* hexdigit

\ de *directive*
&nbsp;&nbsp;&nbsp;&nbsp;*generalDir* | *segmentDef*

*directiveList*\
&nbsp;&nbsp;&nbsp;&nbsp;*directive* | *directiveList*

*distance*\
&nbsp;&nbsp;&nbsp;&nbsp;*nearfar* | **NEAR16** | **NEAR32** | **FAR16** | **FAR32**

*0e01*\
&nbsp;&nbsp;&nbsp;&nbsp;0e01 *orOp* *E02* | *E02*

*e02*\
&nbsp;&nbsp;&nbsp;&nbsp;E02 **et** *E03* | *E03*

*e03*\
&nbsp;&nbsp; **&nbsp;&nbsp;** *E04* | *E04*

*e04*\
&nbsp;&nbsp;&nbsp;&nbsp;*E04* *relOp* *E05* | *E05*

*e05*\
&nbsp;&nbsp;&nbsp;&nbsp;*E05* *addOp* *E06* | *E06*

*e06*\
&nbsp;&nbsp;&nbsp;&nbsp;*E06* *mulOp* *e07* | *E06* *shiftOp* *E07* | *E07*

*e07*\
&nbsp;&nbsp;&nbsp;&nbsp;*E07* *addOp* *E08* | *E08*

*e08*\
&nbsp;&nbsp;&nbsp;&nbsp; *E09* élevé\
&nbsp;&nbsp;&nbsp;&nbsp;|  *E09* faible\
&nbsp;&nbsp;&nbsp;&nbsp;| **highword,** *E09*\
&nbsp;&nbsp;&nbsp;&nbsp;| **lowword,** *E09*\
&nbsp;&nbsp;&nbsp;&nbsp;| *E09*

*e09*\
&nbsp;&nbsp;&nbsp;&nbsp;**décalage** *E10*\
&nbsp;&nbsp;&nbsp;&nbsp;| **SEG** *E10*\
&nbsp;&nbsp;&nbsp;&nbsp;| **lroffset,** *E10*\
&nbsp;&nbsp;&nbsp;&nbsp;| de **type** *E10*\
&nbsp;&nbsp;&nbsp;&nbsp;| **ce** *E10*\
&nbsp;&nbsp;&nbsp;&nbsp;| *E09* **ptr** *E10*\
&nbsp;&nbsp;&nbsp;&nbsp;| *E09* : *E10*\
&nbsp;&nbsp;&nbsp;&nbsp;| *E10*

*e10*\
&nbsp;&nbsp;&nbsp;&nbsp;*E10* . *e11*\
&nbsp;&nbsp;&nbsp;&nbsp;| *E10* ⟦ *expr* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;| *E11*

*e11*\
&nbsp;&nbsp;&nbsp;&nbsp;( *expr* ) \
&nbsp;&nbsp;&nbsp;&nbsp;| ⟦ *expr* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;*ID* de **largeur** | 
&nbsp;&nbsp;&nbsp;&nbsp;*ID* de **masque** | 
&nbsp;&nbsp;&nbsp;&nbsp;sizeArg **Size** | 
&nbsp;&nbsp;&nbsp;&nbsp;| **sizeof** *sizeArg*\
&nbsp;&nbsp;&nbsp;&nbsp;*ID* de **longueur** | 
&nbsp;&nbsp;&nbsp;&nbsp;| **lengthof,** *\*
&nbsp;&nbsp;&nbsp;&nbsp;| *recordConst*\
&nbsp;&nbsp;&nbsp;&nbsp;| *string*\
&nbsp;&nbsp;&nbsp;&nbsp;| *constante*\
&nbsp;&nbsp;&nbsp;&nbsp;*type* | 
&nbsp;&nbsp;&nbsp;&nbsp;| *id*\
&nbsp;&nbsp;&nbsp;&nbsp;| **$**\
&nbsp;&nbsp;&nbsp;&nbsp;| *segmentRegister*\
&nbsp;&nbsp;&nbsp;&nbsp;| *inscrire*\
&nbsp;&nbsp;&nbsp;&nbsp;| **St**\
&nbsp;&nbsp;&nbsp;&nbsp;| **St** ( *expr* )

*echoDir*\
&nbsp;&nbsp;&nbsp;&nbsp;**ECHO**\
&nbsp;&nbsp;&nbsp;&nbsp;*arbitraryText* ;; \
%**out** *arbitraryText* ;; \

*elseifBlock*\
&nbsp;&nbsp;&nbsp;&nbsp;*elseifStatement* ;; \
&nbsp;&nbsp;&nbsp;&nbsp;*directiveList*\
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *elseifBlock* ⟧ \

*elseifStatement*\
&nbsp;&nbsp;&nbsp;&nbsp;**ElseIf** *constExpr*\
&nbsp;&nbsp;&nbsp;&nbsp;| **ELSEIFE** *constExpr*\
&nbsp;&nbsp;&nbsp;&nbsp;| **ELSEIFB** *textItem*\
&nbsp;&nbsp;&nbsp;&nbsp;| **ELSEIFNB** *textItem*\
&nbsp;&nbsp;&nbsp;&nbsp;| **elseifdef (** *\*
&nbsp;&nbsp;&nbsp;&nbsp;| **elseifndef (** *\*
&nbsp;&nbsp;&nbsp;&nbsp;| **ELSEIFDIF** *textItem* , *textItem*\
&nbsp;&nbsp;&nbsp;&nbsp;| **ELSEIFDIFI** *textItem* , *textItem*\
&nbsp;&nbsp;&nbsp;&nbsp;| **ELSEIFIDN** *textItem* , *textItem*\
&nbsp;&nbsp;&nbsp;&nbsp;| **ELSEIFIDNI** *textItem* , *textItem*\
&nbsp;&nbsp;&nbsp;&nbsp;| **ELSEIF1**\
&nbsp;&nbsp;&nbsp;&nbsp;| **ELSEIF2**

*endDir*\
&nbsp;&nbsp;&nbsp;&nbsp;**end** ⟦ *immExpr* ⟧;;

*endpDir*\
&nbsp;&nbsp;&nbsp;&nbsp;*procId* **ENDP** ;;

*endsDir*\
&nbsp;&nbsp;&nbsp;*ID* de &nbsp;**se termine** ;;

*equDir*\
&nbsp;&nbsp;&nbsp;&nbsp;*textMacroId* **Equ** *equType* ;;

*equType*\
&nbsp;&nbsp;&nbsp;&nbsp;*immExpr* | *textLiteral*

*errorDir*\
&nbsp;&nbsp;&nbsp;&nbsp;*errorOpt* ;;

*errorOpt*\
&nbsp;&nbsp;&nbsp;&nbsp; **. ERR** ⟦ *textItem* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;|  **. ERRE** *constExpr* ⟦ *optText* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;|  **. ERRNZ** *constExpr* ⟦ *optText* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;|  **. ERRB** *textItem* ⟦ *optText* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;|  **. ERRNB** *textItem* ⟦ *optText* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;|  **. ERRDEF** *ID* ⟦ *optText* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;|  **. ERRNDEF** *ID* ⟦ *optText* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;|  **. ERRDIF** *textItem* , *textItem* ⟦ *optText* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;|  **. ERRDIFI** *textItem* , *textItem* ⟦ *optText* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;|  **. ERRIDN** *textItem* , *textItem* ⟦ *optText* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;|  **. ERRIDNI** *textItem* , *textItem* ⟦ *optText* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;|  **. ERR1** ⟦ *textItem* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;|  **. ERR2** ⟦ *textItem* ⟧

*exitDir*\
&nbsp;&nbsp;&nbsp;&nbsp; **. EXIT** &nbsp;&nbsp;&nbsp;&nbsp;⟦ *expr* ⟧;;

*exitmDir*\
&nbsp;&nbsp;&nbsp;&nbsp;: quitter | QUITTER *textItem*

*exposant*\
&nbsp;&nbsp;&nbsp;&nbsp;*E ⟦ ⟧* *decNumber*

*expr*\
&nbsp;&nbsp;&nbsp;&nbsp;**short** *E05*\
&nbsp;&nbsp;&nbsp;&nbsp;|  **. TAPEZ** 0e01 \
&nbsp;&nbsp;&nbsp;&nbsp;| **opattr,** *0e01*\
&nbsp;&nbsp;&nbsp;&nbsp;| *0e01*

*exprList*\
&nbsp;&nbsp;&nbsp;&nbsp;*expr* | *exprList* , *expr*

*externDef*\
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *langType* ⟧ *ID* ⟦ ( *altId* ) ⟧ : *externType*

*externDir*\
&nbsp;&nbsp;&nbsp;&nbsp;*externKey* *externList* ;;

*externKey*\
&nbsp;&nbsp;&nbsp;&nbsp;**EXTRN** | **extern** | **EXTERNDEF**

*externList*\
&nbsp;&nbsp;&nbsp;&nbsp;*externDef* | *externList* , ⟦;; ⟧ *externDef*

*externType*\
&nbsp;&nbsp;&nbsp;&nbsp;**ABS** | *qualifiedType*

*fieldAlign*\
&nbsp;&nbsp;&nbsp;&nbsp;*constExpr*

*fieldInit*\
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *initValue* ⟧ | *structInstance*

*fieldInitList*\
&nbsp;&nbsp;&nbsp;&nbsp;*fieldInit* | *fieldInitList* , ⟦;; ⟧ *fieldInit*

*fileChar*\
&nbsp;&nbsp;&nbsp;*délimiteur* de &nbsp;

*fileCharList*\
&nbsp;&nbsp;&nbsp;&nbsp;*fileChar* | *fileCharList* *fileChar*

\ de *spécification*
&nbsp;&nbsp;&nbsp;&nbsp;*fileCharList* | *textLiteral*

*flagName*\
&nbsp;&nbsp;&nbsp;&nbsp;**zéro ?** | **transporter ?** | **débordement ?** | le **signe ?** | de **parité ?**

*floatNumber*\
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *Sign* ⟧ *decNumber* . ⟦ *decNumber* ⟧ ⟦ *exposant* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;| *chiffres* R | *chiffres* r

*forcDir*\
&nbsp;&nbsp;&nbsp;&nbsp;**fichi** | **irpc**

*forDir*\
&nbsp;&nbsp;&nbsp;&nbsp;**pour** | **IRP**

*forParm*\
&nbsp;&nbsp;&nbsp;&nbsp;*ID* ⟦ : *forParmType* ⟧

*forParmType*\
&nbsp;&nbsp;&nbsp;&nbsp;**req** | = *textLiteral*

*fpuRegister*\
&nbsp;&nbsp;&nbsp;&nbsp;**St** *expr*

*frameExpr*\
&nbsp;&nbsp;&nbsp;&nbsp; *id* de segment\
&nbsp;&nbsp;&nbsp;&nbsp;| **Dgroup** : *ID*\
&nbsp;&nbsp;&nbsp;&nbsp;| *segmentRegister* : *ID*\
&nbsp;&nbsp;&nbsp;&nbsp;*ID* de | 

*generalDir*\
&nbsp;&nbsp;&nbsp;&nbsp;*modelDir* | *segOrderDir* | *nameDir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *includeLibDir* | *commentDir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *groupDir* | *assumeDir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *structDir* | *recordDir* | *typedefDir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *externDir* | *publicDir* | *commDir* | *protoTypeDir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *equDir* | = Rép | *textDir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *contextDir* | *optionDir* | *processorDir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *radixDir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *titleDir* | *pageDir* | *listDir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *crefDir* | *echoDir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *ifDir* | *errorDir* | *includeDir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *macroDir* | *macroCall* | *macroRepeat* | *purgeDir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *macroWhile* | *macroFor* | *macroForc*\
&nbsp;&nbsp;&nbsp;&nbsp;| *aliasDir*

*gpRegister*\
&nbsp;&nbsp;&nbsp;&nbsp;AX | EAX | CX | ECX | DX | EDX | BX | EBX | DI | EDI | SI | ESI | BP | EBP | SP | ESP | RSP | R8W | R8D | R9W | R9D | R12D | R13W | R13D | R14W | R14D

*groupDir*\
&nbsp;&nbsp;&nbsp;&nbsp; **groupe** GroupID *segIdList*

\ *GroupID*
&nbsp;&nbsp;&nbsp;*ID* de &nbsp;

*hexdigit*\
&nbsp;&nbsp;&nbsp;&nbsp;a | b | c | d | e | f | A | B | C | D | E | FA

*id*\
&nbsp;&nbsp;&nbsp;&nbsp;le premier caractère de l’identificateur peut être un caractère alphabétique majuscule ou minuscule (`[A–Za-z]`) ou l’un de ces quatre caractères : `@ _ $ ?` les caractères restants peuvent être l’un des mêmes caractères ou un chiffre décimal (`[0–9]`). La longueur maximale est de 247 caractères.

*idList*\
&nbsp;&nbsp;&nbsp;&nbsp;*id* | *idList* , *ID*

*ifDir*\
&nbsp;&nbsp;&nbsp;&nbsp;*ifStatement* ;; \
&nbsp;&nbsp;&nbsp;&nbsp;*directiveList*\
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *elseifBlock* ⟧ \
&nbsp;&nbsp;&nbsp; **&nbsp;⟦;;** \
&nbsp;&nbsp;&nbsp;&nbsp;*directiveList* ⟧;; \

*ifStatement*\
&nbsp;&nbsp;&nbsp;&nbsp;**si** *constExpr*\
&nbsp;&nbsp;&nbsp;&nbsp;| **IFE** *constExpr*\
&nbsp;&nbsp;&nbsp;&nbsp;|  *textItem* -appel d’offres\
&nbsp;&nbsp;&nbsp;&nbsp;| **IFNB** *textItem*\
&nbsp;&nbsp;&nbsp;&nbsp;| **ifdef** *ID*\
&nbsp;&nbsp;&nbsp;&nbsp;| **ifndef** *ID*\
&nbsp;&nbsp;&nbsp;&nbsp;| **IFDIF** *textItem* , *textItem*\
&nbsp;&nbsp;&nbsp;&nbsp;| **IFDIFI** *textItem* , *textItem*\
&nbsp;&nbsp;&nbsp;&nbsp;| **IFIDN** *textItem* , *textItem*\
&nbsp;&nbsp;&nbsp;&nbsp;| **IFIDNI** *textItem* , *textItem*\
&nbsp;&nbsp;&nbsp;&nbsp;| **IF1**\
&nbsp;&nbsp;&nbsp;&nbsp;| **IF2**

*immExpr*\
&nbsp;&nbsp;&nbsp;&nbsp;*expr*

*includeDir*\
&nbsp;&nbsp;&nbsp;&nbsp;**include** *;;*

*includeLibDir*\
&nbsp;&nbsp;&nbsp;&nbsp;**includelib (** *;;*

*initValue*\
&nbsp;&nbsp;&nbsp;&nbsp;*immExpr*\
&nbsp;&nbsp;&nbsp;&nbsp;| *string*\
&nbsp;&nbsp;&nbsp;&nbsp;| ? \
&nbsp;&nbsp;&nbsp;&nbsp;| *constExpr* **DUP** ( *scalarInstList* ) \
&nbsp;&nbsp;&nbsp;&nbsp;| *floatNumber*\
&nbsp;&nbsp;&nbsp;&nbsp;| *bcdConst*

*inSegDir*\
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *labelDef* ⟧ *inSegmentDir*

*inSegDirList*\
&nbsp;&nbsp;&nbsp;&nbsp;*inSegDir* | *inSegDirList* *inSegDir*

*inSegmentDir*\
&nbsp;&nbsp;&nbsp;d' *instructions* &nbsp;\
&nbsp;&nbsp;&nbsp;&nbsp;| *dataDir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *controlDir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *startupDir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *exitDir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *offsetDir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *labelDir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *procDir* ⟦ *LocalDirList* ⟧ ⟦ *inSegDirList* ⟧ *endpDir\*
&nbsp;&nbsp;&nbsp;&nbsp;| *invokeDir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *generalDir*

*instrPrefix*\
&nbsp;&nbsp;&nbsp;&nbsp;**REP** | **REPE** | **REPZ** | **REPNE** | **REPNZ** | **Lock**

\ d' *instruction*
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *instrPrefix* ⟧ *asmInstruction*

*invokeArg*\
&nbsp;&nbsp;&nbsp;&nbsp;*Register* :: *register* | *expr* | **addr** *expr*

*invokeDir*\
&nbsp;&nbsp;&nbsp;&nbsp;**appelez** *expr* ⟦, ⟦;; ⟧ *invokeList* ⟧;;

*invokeList*\
&nbsp;&nbsp;&nbsp;&nbsp;*invokeArg* | *invokeList* , ⟦;; ⟧ *invokeArg*

*mot clé*\
&nbsp;&nbsp;&nbsp;&nbsp;tout mot réservé.

*keywordList*\
&nbsp;&nbsp;&nbsp;&nbsp;*mot clé* | *mot clé* *keywordList*

*labelDef*\
&nbsp;&nbsp;&nbsp;&nbsp;*ID* : | *ID* :: | @@:

*labelDir*\
&nbsp;&nbsp;&nbsp;**étiquette** d' *ID* de &nbsp;*qualifiedType* ;;

*langType*\
&nbsp;&nbsp;&nbsp;&nbsp;**C** | **PASCAL** | **Fortran** | de **base** | **syscall** | **StdCall**

*listDir*\
&nbsp;&nbsp;&nbsp;&nbsp;*listOption* ;;

*listOption*\
&nbsp;&nbsp;&nbsp;&nbsp; **. LISTE**\
&nbsp;&nbsp;&nbsp;&nbsp;|  **. Nolist**\
&nbsp;&nbsp;&nbsp;&nbsp;|  **. XLIST**\
&nbsp;&nbsp;&nbsp;&nbsp;|  **. LISTALL**\
&nbsp;&nbsp;&nbsp;&nbsp;|  **. LISTIF**\
&nbsp;&nbsp;&nbsp;&nbsp;|  **. LFCOND**\
&nbsp;&nbsp;&nbsp;&nbsp;|  **. NOLISTIF**\
&nbsp;&nbsp;&nbsp;&nbsp;|  **. SFCOND**\
&nbsp;&nbsp;&nbsp;&nbsp;|  **. TFCOND**\
&nbsp;&nbsp;&nbsp;&nbsp;|  **. LISTMACROALL** |  **. LALL**\
&nbsp;&nbsp;&nbsp;&nbsp;|  **. NOLISTMACRO** |  **. STOUTES**\
&nbsp;&nbsp;&nbsp;&nbsp;|  **. LISTMACRO** |  **. XALL**\

*localDef*\
&nbsp;&nbsp;&nbsp;&nbsp;**local** *idList* ;;

*localDir*\
&nbsp;&nbsp;&nbsp;&nbsp;**local** *parmList* ;;

*localDirList*\
&nbsp;&nbsp;&nbsp;&nbsp;*localDir* | *localDirList* *localDir*

*localList*\
&nbsp;&nbsp;&nbsp;&nbsp;*localDef* | *localList* *localDef*

*macroArg*\
 % *constExpr*\
&nbsp;&nbsp;&nbsp;&nbsp;| %*textMacroId*\
&nbsp;&nbsp;&nbsp;&nbsp;| %*macroFuncId* ( *macroArgList* ) \
&nbsp;&nbsp;&nbsp;&nbsp;| *string*\
&nbsp;&nbsp;&nbsp;&nbsp;| *arbitraryText*\
&nbsp;&nbsp;&nbsp;&nbsp;| < *arbitraryText* >

*macroArgList*\
&nbsp;&nbsp;&nbsp;&nbsp;*macroArg* | *macroArgList* , *macroArg*

*macroBody*\
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *localList* ⟧ *macroStmtList*

*macroCall*\
&nbsp;&nbsp;&nbsp;&nbsp;*ID* *macroArgList* ;; \
&nbsp;&nbsp;&nbsp;&nbsp;*ID* de | ( *macroArgList* )

*macroDir*\
&nbsp;&nbsp; *&nbsp;&nbsp;⟦* *macroParmList* ⟧;; \
&nbsp;&nbsp;&nbsp;&nbsp;*macroBody*\
&nbsp;&nbsp;&nbsp;&nbsp;**ENDM** ;;

*macroFor*\
&nbsp;&nbsp;&nbsp;&nbsp;*forDir* *ForParm* , < *macroArgList* >;; \
&nbsp;&nbsp;&nbsp;&nbsp;*macroBody*\
&nbsp;&nbsp;&nbsp;&nbsp;**ENDM** ;;

*macroForc*\
&nbsp;&nbsp;&nbsp;&nbsp;*forcDir* *ID* , *textLiteral* ;; \
&nbsp;&nbsp;&nbsp;&nbsp;*macroBody*\
&nbsp;&nbsp;&nbsp;&nbsp;**ENDM** ;;

*macroFuncId*\
&nbsp;&nbsp;&nbsp;*ID* de &nbsp;

*macroId*\
&nbsp;&nbsp;&nbsp;&nbsp;*macroProcId* | *macroFuncId*

*macroIdList*\
&nbsp;&nbsp;&nbsp;&nbsp;*macroId* | *macroIdList* , *macroId*

*macroLabel*\
&nbsp;&nbsp;&nbsp;*ID* de &nbsp;

*macroParm*\
&nbsp;&nbsp;&nbsp;&nbsp;*ID* ⟦ : *parmType* ⟧

*macroParmList*\
&nbsp;&nbsp;&nbsp;&nbsp;*macroParm* | *macroParmList* , ⟦;; ⟧ *macroParm*

*macroProcId*\
&nbsp;&nbsp;&nbsp;*ID* de &nbsp;

*macroRepeat*\
&nbsp;&nbsp;&nbsp;&nbsp;*repeatDir* *constExpr* ;; \
&nbsp;&nbsp;&nbsp;&nbsp;*macroBody*\
&nbsp;&nbsp;&nbsp;&nbsp;**ENDM** ;;

*macroStmt*\
&nbsp;&nbsp;&nbsp;*directive* &nbsp; \
&nbsp;&nbsp;&nbsp;&nbsp;| *exitmDir*\
&nbsp;&nbsp;&nbsp;&nbsp;| : *macroLabel*\
&nbsp;&nbsp;&nbsp;&nbsp;| **GOTO**\
&nbsp;&nbsp;&nbsp;&nbsp;*macroLabel*

*macroStmtList*\
&nbsp;&nbsp;&nbsp;&nbsp;*macroStmt* ;; \
&nbsp;&nbsp;&nbsp;&nbsp;| *macroStmtList* *macroStmt* ;; \

*macroWhile*\
&nbsp;&nbsp;&nbsp;&nbsp;**while** *constExpr* ;; \
&nbsp;&nbsp;&nbsp;&nbsp;*macroBody*\
&nbsp;&nbsp;&nbsp;&nbsp;**ENDM** ;;

*mapType*\
&nbsp;&nbsp;&nbsp;&nbsp;**tous** | **aucun** | **NOTPUBLIC**

*memOption*\
&nbsp;&nbsp;&nbsp;&nbsp;**minuscule** | **petite** | **moyenne** | **compact** | **grande** |  grande | **plate**

*mnémonique*\
&nbsp;&nbsp;&nbsp;&nbsp;nom d’instruction.

*modelDir*\
&nbsp;&nbsp;&nbsp;&nbsp; **.** \ de modèle
&nbsp;&nbsp;&nbsp;&nbsp;*memOption* ⟦, *modelOptlist* ⟧;;

*modelOpt*\
&nbsp;&nbsp;&nbsp;&nbsp;*langType* | *stackOption*

*modelOptlist*\
&nbsp;&nbsp;&nbsp;&nbsp;*modelOpt* | *modelOptlist* , *modelOpt*

*module*\
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *directiveList* ⟧ *endDir*

*mulOp*\
&nbsp;&nbsp;&nbsp;&nbsp;\* | / | **Mod**

*nameDir*\
&nbsp;&nbsp;&nbsp;**nom** de &nbsp;\
&nbsp;&nbsp;&nbsp;&nbsp;*ID* ;; \

*nearfar*\
&nbsp;&nbsp;&nbsp;&nbsp;**presque** | 

*nestedStruct*\
&nbsp;&nbsp;&nbsp;&nbsp;*structHdr* ⟦ *ID* ⟧;; \
&nbsp;&nbsp;&nbsp;&nbsp;*structBody*\
&nbsp;&nbsp;&nbsp;&nbsp;**se termine** ;; \

*offsetDir*\
&nbsp;&nbsp;&nbsp;&nbsp;*offsetDirType* ;;

*offsetDirType*\
&nbsp;&nbsp;&nbsp;&nbsp;**même** | **org** *immExpr* | **Aligner** ⟦ *constExpr* ⟧

*offsetType*\
&nbsp;&nbsp;&nbsp;&nbsp;**groupe** | **segment** | **plat**

*oldRecordFieldList*\
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *constExpr* ⟧ | *oldRecordFieldList* , ⟦ *constExpr* ⟧

*optionDir*\
&nbsp;&nbsp;&nbsp;&nbsp;**option** *optionList* ;;

*optionItem*\
&nbsp;&nbsp;&nbsp;&nbsp;**CASEMAP** : *mapType*\
&nbsp;&nbsp;&nbsp;&nbsp;| **DOTNAME** | **NODOTNAME**\
&nbsp;&nbsp;&nbsp;&nbsp;de l’émulateur **|  | **
&nbsp;&nbsp;&nbsp;&nbsp;| **épilogue** : *macroId*\
&nbsp;&nbsp;&nbsp;&nbsp;| **EXPR16** | **EXPR32**\
&nbsp;&nbsp;&nbsp;&nbsp;| **Language** : *langType*\
&nbsp;&nbsp;&nbsp;&nbsp;| **LJMP**
| **NOLJMP**\
&nbsp;&nbsp;&nbsp;&nbsp;| **M510** | **NOM510**\
&nbsp;&nbsp;&nbsp;&nbsp;| **noKeyword** : < *keywordList* >\
&nbsp;&nbsp;&nbsp;&nbsp;| **NOSIGNEXTEND**\
&nbsp;&nbsp;&nbsp;&nbsp;**OFFSET** | : *offsetType*\
&nbsp;&nbsp;&nbsp;&nbsp;| **OLDMACROS** | **NOOLDMACROS**\
&nbsp;&nbsp;&nbsp;&nbsp;| **OLDSTRUCTS** | **NOOLDSTRUCTS**\
&nbsp;&nbsp;&nbsp;&nbsp;| **proc** : *oVisibility*\
&nbsp;&nbsp;&nbsp;&nbsp;**prologue** | *macroId*
&nbsp;&nbsp;&nbsp;&nbsp;| **ReadOnly** | **noreadonly**\
&nbsp;&nbsp;&nbsp;&nbsp;| **étendue** | nolimited **\**
&nbsp;&nbsp;&nbsp;&nbsp;| **segment** : *segSize*\
&nbsp;&nbsp;&nbsp;&nbsp;| **SETIF2** : bool

*optionList*\
&nbsp;&nbsp;&nbsp;&nbsp;*optionItem* | *optionList* , ⟦;; ⟧ *optionItem*

*optText*\
&nbsp;&nbsp;&nbsp;&nbsp;, *textItem*

*orOp*\
&nbsp;&nbsp;&nbsp;&nbsp;**ou** | **Xor**

*oVisibility*\
&nbsp;&nbsp;&nbsp;&nbsp;**PUBLIC** | **exportation** **privée**

*pageDir*\
&nbsp;&nbsp;&nbsp;&nbsp;**page** ⟦ *pageExpr* ⟧;;

*pageExpr*\
&nbsp;&nbsp;&nbsp;&nbsp;\+ | ⟦ *pageLength* ⟧ ⟦, *PageWidth* ⟧

*pageLength*\
&nbsp;&nbsp;&nbsp;&nbsp;*constExpr*

*pageWidth*\
&nbsp;&nbsp;&nbsp;&nbsp;*constExpr*

*param*\
&nbsp;&nbsp;&nbsp;&nbsp;*parmid* ⟦ : *qualifiedType* ⟧ | *parmid* ⟦ *constExpr* ⟧ ⟦ : *qualifiedType* ⟧

*parmId*\
&nbsp;&nbsp;&nbsp;*ID* de &nbsp;

*parmList*\
&nbsp;&nbsp;&nbsp;&nbsp;*param* | *parmList* , ⟦;; *param* ⟧

*parmType*\
&nbsp;&nbsp;&nbsp;&nbsp;**req** | = *textLiteral* | **vararg**

*pOptions*\
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *distance* ⟧ ⟦ *langType* *⟧ ⟦ oVisibility* ⟧

\ *principal*
&nbsp;&nbsp;&nbsp;&nbsp;*expr* *BinaryOp* *expr* | *flagname* | *expr*

*procDir*\
&nbsp;&nbsp;&nbsp;&nbsp;de la **procédure** *procId*\
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *pOptions* ⟧ ⟦ < *macroArgList* > ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *usesRegs* ⟧ ⟦ *procParmList* ⟧

\ du *processeur*
&nbsp;&nbsp;&nbsp;&nbsp;|. 386 |. 386p |. 486 |. 486P \
&nbsp;&nbsp;&nbsp;&nbsp;|. 586 |. 586P |. 686 |. 686P |. 387

*processorDir*\
&nbsp;&nbsp;&nbsp;*processeur* de &nbsp;;; \
&nbsp;&nbsp;&nbsp;| &nbsp;*coprocesseur* ;;

\ *procId*
&nbsp;&nbsp;&nbsp;*ID* de &nbsp;

\ *ProCite*
&nbsp;&nbsp;&nbsp;&nbsp;*instrPrefix* | *dataDir* | *labelDir* | *offsetDir* | *generalDir*

*procParmList*\
&nbsp;&nbsp;&nbsp;&nbsp;⟦, ⟦;; ⟧ *parmList* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;⟦, ⟦;; ⟧ *parmid* : vararg ⟧

*protoArg*\
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *ID* ⟧ : *qualifiedType*

*protoArgList*\
&nbsp;&nbsp;&nbsp;&nbsp;⟦, ⟦;; ⟧ *protoList* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;⟦, ⟦;; ⟧ ⟦ *ID* ⟧ : vararg ⟧

*protoList*\
&nbsp;&nbsp;&nbsp;&nbsp;*protoArg*\
&nbsp;&nbsp;&nbsp;&nbsp;| *protoList* , ⟦;; ⟧ *protoArg*

*protoSpec*\
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *distance* ⟧ ⟦ *langType* ⟧ ⟦ *protoArgList ⟧ |* *typeid*

*protoTypeDir*\
&nbsp;&nbsp;&nbsp;&nbsp;*ID* **proto** *protoSpec*

*pubDef*\
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *langType* ⟧

*publicDir*\
&nbsp;&nbsp;&nbsp;&nbsp;**public** *pubList* ;;

*pubList*\
&nbsp;&nbsp;&nbsp;&nbsp;*pubDef* | *pubList* , ⟦;; ⟧ *pubDef*

*purgeDir*\
&nbsp;&nbsp;&nbsp;&nbsp;**purger** *macroIdList*

*qualifiedType*\
&nbsp;&nbsp;&nbsp;*type* de &nbsp;| ⟦ *distance* ⟧ **ptr** ⟦ *qualifiedType* ⟧

*qualificateur*\
&nbsp;&nbsp;&nbsp;&nbsp;*qualifiedType* | **proto** *protoSpec*

*guillemet*\
&nbsp;&nbsp;&nbsp;&nbsp;« | »

*qwordRegister*\
&nbsp;&nbsp;&nbsp;&nbsp;RAX | RCX | RDX | RBX | RDI | RSI | RBP | R8 | R9 | R10 | R11 | R12 | R13 | R14 | R15

*radixDir*\
&nbsp;&nbsp;&nbsp;&nbsp; **. BASE** *constExpr* ;;

*radixOverride*\
&nbsp;&nbsp;&nbsp;&nbsp;h | o | q | t | o | H | O | Q | T | Y

*recordConst*\
&nbsp;&nbsp;&nbsp;&nbsp;*recordTag* { *oldRecordFieldList* } | *recordTag* < *oldRecordFieldList* >

*recordDir*\
&nbsp;&nbsp;&nbsp;&nbsp;*recordTag* **enregistrement** *bitDefList* ;;

*recordFieldList*\
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *constExpr* ⟧ | *recordFieldList* , ⟦;; ⟧ ⟦ *constExpr* ⟧

*recordInstance*\
 {⟦;; ⟧ *recordFieldList* ⟦;; ⟧} \
&nbsp;&nbsp;&nbsp;&nbsp;| < *oldRecordFieldList* >\
&nbsp;&nbsp;&nbsp;&nbsp;| *constExpr* **(** *recordInstance* )

*recordInstList*\
&nbsp;&nbsp;&nbsp;&nbsp;*recordInstance* | *recordInstList* , ⟦;; ⟧ *recordInstance*

*recordTag*\
&nbsp;&nbsp;&nbsp;*ID* de &nbsp;

*inscrire*\
&nbsp;&nbsp;&nbsp;&nbsp;*specialRegister* | *gpRegister* | *byteRegister* | *qwordRegister* |  *fpuRegister* | *SIMDRegister* | *segmentRegister*

*regList*\
&nbsp;&nbsp;&nbsp;&nbsp;*inscrire* le *Registre* | regList

*relOp*\
&nbsp;&nbsp;&nbsp;&nbsp;EQ | NE | LT | LE | GT | &

*repeatBlock*\
&nbsp;&nbsp;&nbsp;&nbsp; **. RÉPÉTER** ;; \
&nbsp;&nbsp;&nbsp;&nbsp;*blockStatements* ;; untilDir ;;

*repeatDir*\
&nbsp;&nbsp;&nbsp;&nbsp;**répéter** | **REPT**

*scalarInstList*\
&nbsp;&nbsp;&nbsp;&nbsp;*initValue* | *scalarInstList* , ⟦;; ⟧ *initValue*

*segAlign*\
&nbsp;&nbsp;&nbsp;&nbsp;**Byte** | **Word** | **DWORD** | **la** **page** | 

*segAttrib*\
&nbsp;&nbsp;&nbsp;&nbsp;**public** | **STACK** | **Common** | **Memory** | **sur** *constExpr* | **Private**

*segDir*\
&nbsp;&nbsp;&nbsp;&nbsp; **.** \ de code
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *segId* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;|  **.** \ de données
&nbsp;&nbsp;&nbsp;&nbsp;|   **. DONNÉES ?** \
&nbsp;&nbsp;&nbsp;&nbsp;|  **. CONSt**\
&nbsp;&nbsp;&nbsp;&nbsp;|  **. FARDATA**⟦ *segId* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;|   **. FARDATA ?** ⟦ *segId* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;|  **. STACK** ⟦ *constExpr* ⟧

*segId*\
&nbsp;&nbsp;&nbsp;*ID* de &nbsp;

*segIdList*\
&nbsp;&nbsp;&nbsp;&nbsp;*segId*\
&nbsp;&nbsp;&nbsp;&nbsp;| *segIdList* , *segId*

*segmentDef*\
&nbsp;&nbsp;&nbsp;&nbsp;*segmentDir* ⟦ *inSegDirList* ⟧ *endsDir* | *simpleSegDir* ⟦ *inSegDirList* ⟧ ⟦ *endsDir* ⟧

*segmentDir*\
&nbsp;&nbsp;&nbsp;&nbsp;*segId* **segment** ⟦ *segOptionList* ⟧;;

*segmentRegister*\
&nbsp;&nbsp;&nbsp;&nbsp;**CS** | **DS** | **ES** | **FS** | **GS** | **SS**

*segOption*\
&nbsp;&nbsp;&nbsp;&nbsp;*segAlign*\
&nbsp;&nbsp;&nbsp;&nbsp;| *segRO*\
&nbsp;&nbsp;&nbsp;&nbsp;| *segAttrib*\
&nbsp;&nbsp;&nbsp;&nbsp;| *segSize*\
&nbsp;&nbsp;&nbsp;&nbsp;| *className*

*segOptionList*\
&nbsp;&nbsp;&nbsp;&nbsp;*segOption* | *segOptionList* *segOption*

*segOrderDir*\
&nbsp;&nbsp;&nbsp;&nbsp; **.**  | alpha **. SEQ** |  **. DOSSEG (**  | **dosseg (**

*segRO*\
&nbsp;&nbsp;&nbsp;&nbsp;**ReadOnly**

*segSize*\
&nbsp;&nbsp;&nbsp;&nbsp;**USE16** | **USE32** | **plat**

*shiftOp*\
&nbsp;&nbsp;&nbsp;&nbsp;**SHR** | **SHL**

*signe*\
 - | +

*simdRegister*\
&nbsp;&nbsp;&nbsp;&nbsp;MM0 | MM1 | MM2 | MM3 | MM4 | MM5 | MM6 | MM7 | xmmRegister | YMM0 | YMM1 | YMM2 | YMM3 | YMM4 | YMM5 | YMM6 | YMM7 | YMM8 | YMM9 | YMM10 | YMM11 | YMM12 | YMM13 | YMM14 | YMM15

*simpleExpr*\
 ( *cExpr* ) | *principal*

*simpleSegDir*\
&nbsp;&nbsp;&nbsp;&nbsp;*segDir* ;;

*sizeArg*\
&nbsp;&nbsp; *&nbsp;&nbsp; | * de *type* | *E10*

*specialChars*\
 : | . | ⟦ | ⟧ | ( | ) | < | > | { | } \
&nbsp;&nbsp;&nbsp;&nbsp;| + | - | / | * | & | % | !\
&nbsp;&nbsp;&nbsp;&nbsp;| ' | \ | = | ; | , | "\
&nbsp;&nbsp;&nbsp;&nbsp;| *whiteSpaceCharacter*\
&nbsp;&nbsp;&nbsp;&nbsp;| *endOfLine*

*specialRegister*\
&nbsp;&nbsp;&nbsp;&nbsp;Registre CR0 | CR2 | CR3 | DR0 | DR1 | DR2 | DR3 | DR6 | DR7 | TR3 | TR4 | TR5 | TR6 | TR7

*stackOption*\
&nbsp;&nbsp;&nbsp;&nbsp;**NEARSTACK** | **FARSTACK**

*startupDir*\
&nbsp;&nbsp;&nbsp;&nbsp; **. DÉMARRAGE** ;;

*stext*\
&nbsp;&nbsp;&nbsp;&nbsp;*stringChar* | *sText* *stringChar*

*string*\
&nbsp;&nbsp;&nbsp;&nbsp;*quot* ⟦ *sText* ⟧

*stringChar*\
&nbsp;&nbsp; *&nbsp;&nbsp;guillemets* *|* N’importe quel caractère sauf quot.

*structBody*\
&nbsp;&nbsp;&nbsp;&nbsp;*structItem* ;; \
&nbsp;&nbsp;&nbsp;&nbsp;| *structBody* *structItem* ;;

*structDir*\
&nbsp;&nbsp;&nbsp;&nbsp;*structTag* *structHdr* ⟦ *fieldAlign* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;⟦, ⟧ non **unique** ;; \
&nbsp;&nbsp;&nbsp;&nbsp;*structBody*\
&nbsp;&nbsp;&nbsp;&nbsp;*structTag*\
&nbsp;&nbsp;&nbsp;&nbsp;**se termine** ;;

*structHdr*\
&nbsp;&nbsp;&nbsp;&nbsp;**STRUC** | **struct** | **Union**

*structInstance*\
 < ⟦ *fieldInitList* ⟧ > \
&nbsp;&nbsp;&nbsp;&nbsp;| {⟦;; ⟧ ⟦ *fieldInitList* ⟧ ⟦;; ⟧} \
&nbsp;&nbsp;&nbsp;&nbsp;| *constExpr* **DUP** ( *structInstList* ) \

*structInstList*\
&nbsp;&nbsp;&nbsp;&nbsp;*structInstance* | *structInstList* , ⟦;; ⟧ *structInstance*

*structItem*\
&nbsp;&nbsp;&nbsp;&nbsp;*dataDir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *generalDir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *offsetDir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *nestedStruct*

*structTag*\
&nbsp;&nbsp;&nbsp;*ID* de &nbsp;

*terme*\
&nbsp;&nbsp;&nbsp;&nbsp;*simpleExpr* | ! *simpleExpr*

*text*\
&nbsp;&nbsp;&nbsp;&nbsp;*textLiteral* |  *|* ! *texte* de caractère | *caractère* | ! *caractère*

*textDir*\
&nbsp;&nbsp;&nbsp;&nbsp;*ID* *textMacroDir* ;;

*textItem*\
&nbsp;&nbsp;&nbsp;&nbsp;*textLiteral* | *textMacroId* | % *constExpr*

*textLen*\
&nbsp;&nbsp;&nbsp;&nbsp;*constExpr*

*textList*\
&nbsp;&nbsp;&nbsp;&nbsp;*textItem* | *textList* , ⟦;; ⟧ *textItem*

*textLiteral*\
&nbsp;&nbsp;&nbsp;&nbsp;< *text* >;;

*textMacroDir*\
&nbsp;&nbsp;&nbsp;&nbsp;**catstr (** ⟦ *textList* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;| **TEXTEQU** ⟦ *textList* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;| **sizestr (** *textItem*\
&nbsp;&nbsp;&nbsp;&nbsp;| **substr** *textItem* , *textStart* ⟦, *textLen* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;| **InStr** ⟦ *TextStart* , ⟧ *textItem* , *textItem*

*textMacroId*\
&nbsp;&nbsp;&nbsp;*ID* de &nbsp;

*textStart*\
&nbsp;&nbsp;&nbsp;&nbsp;*constExpr*

*titleDir*\
&nbsp;&nbsp;&nbsp;&nbsp;*titleType* *arbitraryText* ;;

*titleType*\
&nbsp;&nbsp;&nbsp;&nbsp;**TITLE** |  **SUBTTL**

*type*\
&nbsp;&nbsp;&nbsp;&nbsp;*structTag*\
&nbsp;&nbsp;&nbsp;&nbsp;| *unionTag*\
&nbsp;&nbsp;&nbsp;&nbsp;| *recordTag*\
&nbsp;&nbsp;&nbsp;&nbsp;| *distance*\
&nbsp;&nbsp;&nbsp;&nbsp;*type de données* | 
&nbsp;&nbsp;&nbsp;&nbsp;| *typeid*

*typedefDir*\
qualificateur **TYPEDEF** &nbsp;&nbsp;&nbsp;&nbsp;*typeid*

*typeId*\
&nbsp;&nbsp;&nbsp;*ID* de &nbsp;

*unionTag*\
&nbsp;&nbsp;&nbsp;*ID* de &nbsp;

*untilDir*\
&nbsp;&nbsp;&nbsp;&nbsp; **. JUSQU’à** *cExpr* ;; \
&nbsp;&nbsp;&nbsp;&nbsp; **. UNTILCXZ** ⟦ *cxzExpr* ⟧;;

*usesRegs*\
&nbsp;&nbsp;&nbsp;&nbsp;**utilise** *regList*

*whileBlock*\
&nbsp;&nbsp;&nbsp;&nbsp; **.\**
&nbsp;&nbsp;&nbsp;&nbsp;*cExpr* ;; \
&nbsp;&nbsp;&nbsp;&nbsp;*blockStatements* ;; \
&nbsp;&nbsp;&nbsp;&nbsp; **. ENDW**

*whiteSpaceCharacter*\
&nbsp;&nbsp;&nbsp;&nbsp;ASCII 8, 9, 11-13, 26, 32

*xmmRegister*\
&nbsp;&nbsp;&nbsp;&nbsp;XMM0 | XMM1 | XMM2 | XMM3 | XMM4 | XMM5 | XMM6 | XMM7 | XMM8 | XMM9 | XMM10 | XMM11 | XMM12 | XMM13 | XMM14 | XMM15\

