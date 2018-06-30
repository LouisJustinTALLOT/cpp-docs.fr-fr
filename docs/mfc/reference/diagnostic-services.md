---
title: Services de diagnostic | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.mfc.macros
dev_langs:
- C++
helpviewer_keywords:
- diagnosi [MFC]s, diagnostic services
- diagnostic macros [MFC], list of general MFC
- services [MFC], diagnostic
- MFC, diagnostic services
- general diagnostic functions and variables [MFC]
- diagnostics [MFC], diagnostic functions and variables
- diagnostics [MFC], list of general MFC
- diagnosis [MFC], diagnostic functions and variables
- diagnosis [MFC], list of general MFC
- general diagnostic macros in MFC
- diagnostic macros [MFC]
- diagnostic services [MFC]
- object diagnostic functions in MFC
- diagnostics [MFC], diagnostic services
- diagnostic functions and variables [MFC]
ms.assetid: 8d78454f-9fae-49c2-88c9-d3fabd5393e8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 00aece4445f87ab13b0f3250e6e0b1a337d75633
ms.sourcegitcommit: 208d445fd7ea202de1d372d3f468e784e77bd666
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37122991"
---
# <a name="diagnostic-services"></a>Services de diagnostic
La bibliothèque Microsoft Foundation Class fournit de nombreux services de diagnostic qui simplifient le débogage de vos programmes. Elle propose notamment des macros et des fonctions globales qui vous permettent d’effectuer le suivi des allocations mémoire de votre programme, de vider le contenu des objets au moment de l’exécution et d’afficher des messages de débogage au moment de l’exécution. Les macros et les fonctions globales pour les services de diagnostic sont regroupées dans les catégories suivantes :  
  
-   Macros de diagnostic général  
  
-   Fonctions et variables de diagnostic général  
  
-   Fonctions de diagnostic d’objet  
  
 Ces macros et fonctions sont disponibles pour toutes les classes dérivées de `CObject` dans les versions Debug et Release de MFC. Toutefois, tous sauf DEBUG_NEW et vérifier ne rien faire dans la version Release.  
  
 Dans la bibliothèque Debug, tous les blocs de mémoire alloués sont entourés d’une série d’« octets de protection ». Si ces octets sont perturbés par une écriture en mémoire non contrôlée, les routines de diagnostic peuvent signaler un problème. Si vous incluez la ligne :  
  
 [!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/cpp/diagnostic-services_1.cpp)]  
  
 dans votre fichier d’implémentation, tous les appels à **new** stockent le nom de fichier et le numéro de ligne où l’allocation de mémoire a eu lieu. La fonction [CMemoryState::DumpAllObjectsSince](cmemorystate-structure.md#dumpallobjectssince) affiche ces informations supplémentaires, ce qui vous permet d’identifier les fuites de mémoire. Pour plus d’informations sur la sortie de diagnostic, consultez également la classe [CDumpContext](../../mfc/reference/cdumpcontext-class.md) .  
  
 La bibliothèque Runtime C prend également en charge un ensemble de fonctions de diagnostic que vous pouvez utiliser pour déboguer vos applications. Pour plus d’informations, consultez [Routines de débogage](../../c-runtime-library/debug-routines.md) dans la Référence de la bibliothèque runtime.  
  
### <a name="mfc-general-diagnostic-macros"></a>Macros de diagnostic général MFC  
  
|||  
|-|-|  
|[ASSERT](#assert)|Imprime un message et interrompt le programme si l’expression spécifiée a la valeur FALSE dans la version Debug de la bibliothèque.|  
|[ASSERT_KINDOF](#assert_kindof)|Vérifie qu’un objet est un objet de la classe spécifiée ou d’une classe dérivée de la classe spécifiée.|  
|[ASSERT_VALID](#assert_valid)|Teste la validité interne d’un objet en appelant sa fonction membre `AssertValid` ; généralement substituée à partir de `CObject`.|
|[DEBUG_NEW](#debug_new)|Fournit un nom de fichier et un numéro de ligne pour toutes les allocations d’objets en mode débogage, pour faciliter la recherche des fuites de mémoire.|  
|[DEBUG_ONLY](#debug_only)|Similaire à ASSERT, mais ne teste ne pas la valeur de l’expression. utile pour le code qui doit s’exécuter uniquement en mode débogage.|  
|[Vérifiez et ENSURE_VALID](#ensure)|Utilisez cette option pour valider l’exactitude des données.|
|[THIS_FILE](#this_file)|Développe le nom du fichier qui est compilé.|
|[TRACE](#trace)|Fournit des fonctionnalités semblables à `printf`dans la version Debug de la bibliothèque.|  
|[VERIFY](#verify)|Similaire à ASSERT évalue, mais l’expression dans la version de la bibliothèque, ainsi que dans la version Debug.|  
  
### <a name="mfc-general-diagnostic-variables-and-functions"></a>Fonctions et variables de diagnostic général MFC  
  
|||  
|-|-|  
|[afxDump](#afxdump)|Variable globale qui envoie des informations [CDumpContext](../../mfc/reference/cdumpcontext-class.md) à la fenêtre de sortie du débogueur ou au terminal de débogage.|  
|[afxMemDF](#afxmemdf)|Variable globale qui contrôle le comportement de l’allocateur de mémoire de débogage.|  
|[AfxCheckError](#afxcheckerror)|Variable globale utilisée pour tester le SCODE passé pour voir s’il s’agit d’une erreur et, dans ce cas, génère l’erreur appropriée.|  
|[AfxCheckMemory](#afxcheckmemory)|Vérifie l’intégrité de toute la mémoire allouée actuellement.|  
|[AfxDebugBreak](#afxdebugbreak)|Provoque une rupture dans l’exécution.|
|[AfxDump](#cdumpcontext_in_mfc)|En cas d’appel dans le débogueur, vide l’état d’un objet pendant le débogage.|  
|[AfxDump](#afxdump)|Fonction interne qui exporte l’état d’un objet pendant le débogage.|
|[AfxDumpStack](#afxdumpstack)|Génère une image de la pile actuelle. Cette fonction est toujours liée de manière statique.|  
|[AfxEnableMemoryLeakDump](#afxenablememoryleakdump)|Active le vidage de fuite de mémoire.|  
|[AfxEnableMemoryTracking](#afxenablememorytracking)|Active et désactive le suivi de la mémoire.|  
|[AfxIsMemoryBlock](#afxismemoryblock)|Vérifie qu’un bloc de mémoire a été alloué correctement.|  
|[AfxIsValidAddress](#afxisvalidaddress)|Vérifie qu’une plage d’adresses mémoire est dans les limites du programme.|  
|[AfxIsValidString](#afxisvalidstring)|Détermine si un pointeur vers une chaîne est valide.|  
|[AfxSetAllocHook](#afxsetallochook)|Permet l’appel d’une fonction lors de chaque allocation de mémoire.|  
  
### <a name="mfc-object-diagnostic-functions"></a>Fonctions de diagnostic d’objet MFC  
  
|||  
|-|-|  
|[AfxDoForAllClasses](#afxdoforallclasses)|Exécute une fonction spécifiée sur toutes les classes dérivées de `CObject`qui prennent en charge la vérification du type au moment de l’exécution.|  
|[AfxDoForAllObjects](#afxdoforallobjects)|Exécute une fonction spécifiée sur tous les objets dérivés de `CObject`qui ont été alloués avec **new**.|  

### <a name="mfc-compilation-macros"></a>Compilation des Macros MFC
|||
|-|-|
|[_AFX_SECURE_NO_WARNINGS](#afx_secure_no_warnings)|Supprime les avertissements du compilateur pour l’utilisation des fonctions MFC déconseillées.|  


## <a name="afx_secure_no_warnings"></a> _AFX_SECURE_NO_WARNINGS
Supprime les avertissements du compilateur pour l’utilisation des fonctions MFC déconseillées.  
   
### <a name="syntax"></a>Syntaxe   
```  
_AFX_SECURE_NO_WARNINGS  
```     
### <a name="example"></a>Exemple  
 Cet exemple de code entraîne un avertissement du compilateur si _AFX_SECURE_NO_WARNINGS n’ont pas été définies.  
  
 ```cpp
// define this before including any afx files in stdafx.h
#define _AFX_SECURE_NO_WARNINGS
```
```cpp
CRichEditCtrl* pRichEdit = new CRichEditCtrl;
pRichEdit->Create(WS_CHILD|WS_VISIBLE|WS_BORDER|ES_MULTILINE,
   CRect(10,10,100,200), pParentWnd, 1);
char sz[256];
pRichEdit->GetSelText(sz);
```

## <a name="afxdebugbreak"></a> AfxDebugBreak
Appelez cette fonction pour provoquer un arrêt (à l’emplacement de l’appel à `AfxDebugBreak`) dans l’exécution de la version debug de votre application MFC.  

### <a name="syntax"></a>Syntaxe    
```
void AfxDebugBreak( );    
```  
   
### <a name="remarks"></a>Notes  
 `AfxDebugBreak` dans les versions d’une application MFC n’a aucun effet et doit être supprimé. Cette fonction doit être utilisée uniquement dans les applications MFC. Utilisez la version de l’API Win32, `DebugBreak`, pour provoquer un arrêt dans les applications non-MFC.  
   
### <a name="requirements"></a>Configuration requise  
 **En-tête :** afxver_.h   

##  <a name="assert"></a>  ASSERT
 Évalue son argument.  
  
```   
ASSERT(booleanExpression)   
```  
  
### <a name="parameters"></a>Paramètres  
 *booleanExpression*  
 Spécifie une expression (y compris les valeurs de pointeur) qui prend la valeur zéro ou 0.  
  
### <a name="remarks"></a>Notes  
 Si le résultat est 0, la macro imprime un message de diagnostic et interrompt le programme. Si la condition est différente de zéro, elle ne fait rien.  
  
 Le message de diagnostic se présente sous la forme  
  
 `assertion failed in file <name> in line <num>`  
  
 où *nom* est le nom du fichier source, et *num* est le numéro de ligne de l’assertion a échoué dans le fichier source.  
  
 Dans la version Release de MFC, ASSERT n’évalue l’expression et par conséquent n’interrompt pas le programme. Si l’expression doit être évaluée, quelle que soit l’environnement, utilisez la macro VERIFY à la place d’ASSERT.  
  
> [!NOTE]
>  Cette fonction est disponible uniquement dans la version Debug des MFC.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_Utilities#44](../../mfc/codesnippet/cpp/diagnostic-services_2.cpp)]  

### <a name="requirements"></a>Configuration requise  
 **En-tête :** afx.h 

##  <a name="assert_kindof"></a>  ASSERT_KINDOF  
 Cette macro déclare que l’objet désigné est un objet de la classe spécifiée ou est un objet d’une classe dérivé de la classe spécifiée.  
  
```   
ASSERT_KINDOF(classname, pobject)  
```  
  
### <a name="parameters"></a>Paramètres  
 *classname*  
 Le nom d’un `CObject`-classe dérivée.  
  
 *pObject*  
 Pointeur vers un objet de classe.  
  
### <a name="remarks"></a>Notes  
 Le *pobject* doit être un pointeur vers un objet de paramètre et peut être **const**. L’objet pointé et la classe doit prendre en charge `CObject` les informations de classe d’exécution. Par exemple, pour vous assurer que `pDocument` est un pointeur vers un objet de la `CMyDoc` classe, ou l’une de ses dérivés, vous pouvez le code :  
  
 [!code-cpp[NVC_MFCDocView#194](../../mfc/codesnippet/cpp/diagnostic-services_3.cpp)]  
  
 À l’aide de la `ASSERT_KINDOF` macro est exactement le même que le codage :  
  
 [!code-cpp[NVC_MFCDocView#195](../../mfc/codesnippet/cpp/diagnostic-services_4.cpp)]  
  
 Cette fonction fonctionne uniquement pour les classes déclarées avec le [DECLARE_DYNAMIC] (services.md du modèle objet exécution temps #declare_dynamic ou [DECLARE_SERIAL](run-time-object-model-services.md#declare_serial) (macro).  
  
> [!NOTE]
>  Cette fonction est disponible uniquement dans la version Debug des MFC.  

### <a name="requirements"></a>Configuration requise  
 **En-tête :** afx.h 

##  <a name="assert_valid"></a>  ASSERT_VALID  
 Permet de tester vos hypothèses sur la validité de l’état interne d’un objet.  
  
```   
ASSERT_VALID(pObject)   
```  
  
### <a name="parameters"></a>Paramètres  
 *pObject*  
 Spécifie un objet d’une classe dérivée de `CObject` qui a une version de substitution de la `AssertValid` fonction membre.  
  
### <a name="remarks"></a>Notes  
 ASSERT_VALID appelle la `AssertValid` fonction membre de l’objet passé comme argument.  
  
 Dans la version Release de MFC, ASSERT_VALID ne fait rien. Dans la version Debug, il valide le pointeur, vérifie par rapport à NULL et appelle l’objet propre `AssertValid` fonctions membres. Si une de ces tests échoue, un message d’alerte s’affiche dans la même manière que [ASSERT](#assert).  
  
> [!NOTE]
>  Cette fonction est disponible uniquement dans la version Debug des MFC.  
  
 Pour plus d’informations et d’exemples, consultez [débogage des Applications MFC](/visualstudio/debugger/mfc-debugging-techniques).  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCCObjectSample#19](../../mfc/codesnippet/cpp/diagnostic-services_5.cpp)]  

### <a name="requirements"></a>Configuration requise  
 **En-tête :** afx.h

##  <a name="debug_new"></a>  DEBUG_NEW  
 Permet de rechercher les fuites de mémoire.  
  
```   
#define  new DEBUG_NEW   
```  
  
### <a name="remarks"></a>Notes  
 Vous pouvez utiliser DEBUG_NEW partout dans votre programme que vous utiliseriez normalement le **nouveau** opérateur pour allouer le stockage de segment de mémoire.  
  
 En mode débogage (lorsque le **_DEBUG** symbole est défini), DEBUG_NEW assure le suivi du nom de fichier et numéro de ligne pour chaque objet alloué. Ensuite, lorsque vous utilisez la [CMemoryState::DumpAllObjectsSince](cmemorystate-structure.md#dumpallobjectssince) fonction membre, chaque objet alloué avec DEBUG_NEW s’affiche avec le nom de fichier et numéro de ligne où il a été alloué.  
  
 Pour utiliser DEBUG_NEW, insérez la directive suivante dans vos fichiers sources :  
  
 [!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/cpp/diagnostic-services_1.cpp)]  
  
 Une fois que vous insérez cette directive, le préprocesseur insérera DEBUG_NEW partout où vous utilisez **nouveau**, et MFC fait le reste. Lorsque vous compilez une version release de votre programme, DEBUG_NEW est traduit en une simple **nouveau** opération et les informations de numéro de ligne et de nom de fichier ne sont pas générés.  
  
> [!NOTE]
>  Dans les versions antérieures de MFC (4.1 ou version antérieure) que vous avez besoin de placer la `#define` instruction après toutes les instructions qui a appelé la macro IMPLEMENT_DYNCREATE ou IMPLEMENT_SERIAL. Cela n’est plus nécessaire.  

### <a name="requirements"></a>Configuration requise  
 **En-tête :** afx.h

##  <a name="debug_only"></a>  DEBUG_ONLY  
 En mode débogage (lorsque le **_DEBUG** symbole est défini), DEBUG_ONLY évalue son argument.  
  
```   
DEBUG_ONLY(expression)   
```  
  
### <a name="remarks"></a>Notes  
 Dans une version Release, DEBUG_ONLY n’évalue pas son argument. Cela est utile lorsque vous avez du code qui doit être exécuté uniquement dans les versions debug.  
  
 La macro DEBUG_ONLY est équivalente à entourant *expression* avec `#ifdef _DEBUG` et `#endif`.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_Utilities#32](../../mfc/codesnippet/cpp/diagnostic-services_6.cpp)]  

### <a name="requirements"></a>Configuration requise  
 **En-tête :** afx.h

 ### <a name="ensure"></a>  Vérifiez et ENSURE_VALID
Utilisez cette option pour valider l’exactitude des données.  
   
### <a name="syntax"></a>Syntaxe    
```
ENSURE(  booleanExpression )  
ENSURE_VALID( booleanExpression  )  
```
### <a name="parameters"></a>Paramètres  
 *booleanExpression*  
 Spécifie une expression booléenne à tester.  
   
### <a name="remarks"></a>Notes  
 Ces macros vise à améliorer la validation des paramètres. Les macros empêchent le traitement des paramètres incorrects dans votre code. Contrairement aux macros ASSERT, les macros Assurez-vous lèvent une exception en plus de générer une assertion.  
  
 Les macros se comportent de deux façons, selon la configuration de projet. Les macros appellent ASSERT et une exception si l’assertion échoue. Ainsi, dans les configurations de débogage (autrement dit, où _DEBUG est défini) les macros génèrent une assertion et une exception lors de dans les configurations Release, produit macros uniquement l’exception (ASSERT n’évalue l’expression dans les configurations Release).  
  
 La macro ENSURE_ARG agit comme la macro Vérifiez.  
  
 ENSURE_VALID appelle la macro ASSERT_VALID (qui a un effet uniquement dans les versions Debug). En outre, ENSURE_VALID lève une exception si le pointeur est NULL. Le test de la valeur NULL est effectué dans les configurations Debug et Release.  
  
 Si un de ces tests échoue, un message d’alerte s’affiche dans la même manière que l’assertion. La macro lève une exception d’argument non valide si nécessaire.  
### <a name="requirements"></a>Configuration requise  
 **En-tête :** afx.h  
   
### <a name="see-also"></a>Voir aussi  
 [Macros et objet Globals](mfc-macros-and-globals.md)   
 [VÉRIFIER](#verify)   
 [ATLENSURE](#altensure)

## <a name="this_file"></a> THIS_FILE
Développe le nom du fichier qui est compilé.  
   
### <a name="syntax"></a>Syntaxe    
```
THIS_FILE    
```  
   
### <a name="remarks"></a>Notes  
 Les informations sont utilisées par les macros ASSERT et à vérifier. Les Assistants code et Assistant Application placer la macro dans les fichiers de code source qu’ils créent.  
   
### <a name="example"></a>Exemple  
```cpp
#ifdef _DEBUG
#undef THIS_FILE
static char THIS_FILE[] = __FILE__;
#endif

// __FILE__ is one of the six predefined ANSI C macros that the 
// compiler recognizes. 
```
   
### <a name="requirements"></a>Configuration requise  
 **En-tête :** afx.h  
   
### <a name="see-also"></a>Voir aussi  
 [Macros et objet Globals](mfc-macros-and-globals.md)   
 [ASSERT](#assert)   
 [VERIFY](#verify)


##  <a name="trace"></a>  TRACE  
 Envoie la chaîne spécifiée dans le débogueur de l’application actuelle.  
  
```   
TRACE(exp)  
TRACE(DWORD  category,  UINT  level, LPCSTR lpszFormat, ...)   
```  
  
### <a name="remarks"></a>Notes  
 Consultez [ATLTRACE2](../../atl/reference/debugging-and-error-reporting-macros.md#atltrace2) pour obtenir une description de la TRACE. SUIVI et ATLTRACE2 ont le même comportement.  
  
 Dans la version debug des MFC, cette macro envoie la chaîne spécifiée dans le débogueur de l’application actuelle. Dans une version Release, cette macro est compilé en nothing (aucun code n’est effectivement générée).  
  
 Pour plus d’informations, consultez [débogage des Applications MFC](/visualstudio/debugger/mfc-debugging-techniques).  

### <a name="requirements"></a>Configuration requise  
 **En-tête :** afx.h

##  <a name="verify"></a>  VERIFY  
 Dans la version Debug des MFC, évalue son argument.  
  
```   
VERIFY(booleanExpression)   
```  
  
### <a name="parameters"></a>Paramètres  
 *booleanExpression*  
 Spécifie une expression (y compris les valeurs de pointeur) qui prend la valeur zéro ou 0.  
  
### <a name="remarks"></a>Notes  
 Si le résultat est 0, la macro imprime un message de diagnostic et interrompt le programme. Si la condition est différente de zéro, elle ne fait rien.  
  
 Le message de diagnostic se présente sous la forme  
  
 `assertion failed in file <name> in line <num>`  
  
 où *nom* est le nom du fichier source et *num* est le numéro de ligne de l’assertion a échoué dans le fichier source.  
  
 Dans la version Release de MFC, vérifiez évalue l’expression, mais ne pas imprimer ou interrompre le programme. Par exemple, si l’expression est un appel de fonction, l’appel effectué.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCDocView#198](../../mfc/codesnippet/cpp/diagnostic-services_7.cpp)]  

### <a name="requirements"></a>Configuration requise  
 **En-tête :** afx.h

##  <a name="cdumpcontext_in_mfc"></a>  afxDump (CDumpContext dans MFC)  
 Fournit une fonctionnalité base de dump d’objets dans votre application.  
  
```   
CDumpContext  afxDump;   
```  
  
### <a name="remarks"></a>Notes  
 `afxDump` est prédéfini [CDumpContext](../../mfc/reference/cdumpcontext-class.md) objet qui vous permet d’envoyer `CDumpContext` les informations dans la fenêtre de sortie du débogueur ou à un terminal de débogage. En règle générale, vous fournissez `afxDump` en tant que paramètre à `CObject::Dump`.  
  
 Sous Windows NT et toutes les versions de Windows, `afxDump` sortie est envoyée à la fenêtre de sortie de débogage de Visual C++, lorsque vous déboguez votre application.  
  
 Cette variable est définie uniquement dans la version Debug des MFC. Pour plus d’informations sur `afxDump`, consultez [débogage des Applications MFC](/visualstudio/debugger/mfc-debugging-techniques).  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_Utilities#23](../../mfc/codesnippet/cpp/diagnostic-services_8.cpp)]  

### <a name="requirements"></a>Configuration requise  
 **En-tête :** afx.h


## <a name="afxdump"></a> AfxDump (interne)
Fonction interne qui utilise des MFC pour vider l’état d’un objet pendant le débogage.  

### <a name="syntax"></a>Syntaxe    
```
void AfxDump(const CObject* pOb);   
```
### <a name="parameters"></a>Paramètres  
 *boîte postale*  
 Un pointeur vers un objet d’une classe dérivée de `CObject`.  
   
### <a name="remarks"></a>Notes  
 `AfxDump` appelle un objet `Dump` fonction membre et envoie les informations à l’emplacement spécifiées par le `afxDump` variable. `AfxDump` est disponible uniquement dans la version Debug des MFC.  
  
 Code de votre programme ne doit pas appeler `AfxDump`, mais vous devez appeler à la place la `Dump` fonction membre de l’objet approprié.  
   
### <a name="requirements"></a>Configuration requise  
 **En-tête :** afx.h  
   
### <a name="see-also"></a>Voir aussi  
 [CObject::Dump](cobject-class.md#dump)   



##  <a name="afxmemdf"></a>  afxMemDF  
 Cette variable est accessible à partir d’un débogueur ou de votre programme et vous permet de paramétrer les diagnostics d’allocation.  
  
```   
int  afxMemDF;  
```  
  
### <a name="remarks"></a>Notes  
 `afxMemDF` peut avoir les valeurs suivantes comme spécifié par l’énumération `afxMemDF`:  
  
- `allocMemDF` Activer l’allocateur de débogage (paramètre par défaut dans la bibliothèque de débogage).  
  
- `delayFreeMemDF` Retards de la libération de mémoire. Pendant que votre programme libère un bloc de mémoire, l’allocateur ne retourne pas que la mémoire pour le système d’exploitation sous-jacent. Les contraintes de mémoire maximale sera placé sur votre programme.  
  
- `checkAlwaysMemDF` Appels `AfxCheckMemory` chaque fois que mémoire est allouée ou libérée. Cela ralentit considérablement désallocations et les allocations de mémoire.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_Utilities#30](../../mfc/codesnippet/cpp/diagnostic-services_9.cpp)]  

### <a name="requirements"></a>Configuration requise  
 **En-tête :** afx.h

##  <a name="afxcheckerror"></a>  AfxCheckError  
 Cette fonction teste le SCODE passé pour voir s’il s’agit d’une erreur.  
  
```   
void AFXAPI AfxCheckError(SCODE sc);
throw CMemoryException* 
throw COleException*  
```  
  
### <a name="remarks"></a>Notes  
 S’il s’agit d’une erreur, la fonction lève une exception. Si le SCODE passé est E_OUTOFMEMORY, la fonction lève un [CMemoryException](../../mfc/reference/cmemoryexception-class.md) en appelant [AfxThrowMemoryException](exception-processing.md#afxthrowmemoryexception). Sinon, la fonction lève un [COleException](../../mfc/reference/coleexception-class.md) en appelant [AfxThrowOleException](exception-processing.md#afxthrowoleexception).  
  
 Cette fonction peut être utilisée pour vérifier les valeurs de retour d’appels de fonctions OLE dans votre application. En testant la valeur de retour avec cette fonction dans votre application, vous pouvez correctement réagir aux conditions d’erreur avec un minimum de code.  
  
> [!NOTE]
>  Cette fonction a le même effet en mode débogage et non-Debug.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCOleContainer#33](../../mfc/codesnippet/cpp/diagnostic-services_10.cpp)]  

### <a name="requirements"></a>Configuration requise  
 **En-tête :** afx.h

##  <a name="afxcheckmemory"></a>  AfxCheckMemory  
 Cette fonction valide du pool de mémoire libre et imprime les messages d’erreur en fonction des besoins.  
  
```   
BOOL  AfxCheckMemory(); 
```  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si aucune erreur de mémoire ; Sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Si la fonction ne détecte aucune altération de la mémoire, il imprime rien.  
  
 Tous les blocs de mémoire actuellement allouées sur le tas sont vérifiées, y compris celles allouée par **nouveau** mais pas ceux allouée par des appels directs à des allocateurs de mémoire sous-jacente, telles que la **malloc** (fonction) ou le `GlobalAlloc` fonction Windows. Si un bloc est endommagé, un message est écrit dans la sortie du débogueur.  
  
 Si vous incluez la ligne  
  
 [!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/cpp/diagnostic-services_1.cpp)]  
  
 dans un module de programme, les appels suivants à `AfxCheckMemory` afficher le nom de fichier et numéro de ligne où la mémoire a été allouée.  
  
> [!NOTE]
>  Si votre module contient une ou plusieurs implémentations de classes sérialisables, vous devez placer la `#define` ligne après le dernier appel de la macro IMPLEMENT_SERIAL.  
  
 Cette fonction fonctionne uniquement dans la version Debug des MFC.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCCObjectSample#26](../../mfc/codesnippet/cpp/diagnostic-services_11.cpp)]  

### <a name="requirements"></a>Configuration requise  
 **En-tête :** afx.h  
 
##  <a name="afxdump"></a>  AfxDump (MFC)  
 Appelez cette fonction dans le débogueur pour vider l’état d’un objet pendant le débogage.  
  
```   
void AfxDump(const CObject* pOb); 
```  
  
### <a name="parameters"></a>Paramètres  
 *boîte postale*  
 Un pointeur vers un objet d’une classe dérivée de `CObject`.  
  
### <a name="remarks"></a>Notes  
 `AfxDump` appelle un objet `Dump` fonction membre et envoie les informations à l’emplacement spécifiées par le `afxDump` variable. `AfxDump` est disponible uniquement dans la version Debug des MFC.  
  
 Code de votre programme ne doit pas appeler `AfxDump`, mais vous devez appeler à la place la `Dump` fonction membre de l’objet approprié.  

### <a name="requirements"></a>Configuration requise  
 **En-tête :** afx.h  

### <a name="see-also"></a>Voir aussi  
 [CObject::Dump](cobject-class.md#dump)   


  
##  <a name="afxdumpstack"></a>  AfxDumpStack  
 Cette fonction globale peut être utilisée pour générer une image de la pile actuelle.  
  
```   
void AFXAPI AfxDumpStack(DWORD dwTarget = AFX_STACK_DUMP_TARGET_DEFAULT); 
```  
  
### <a name="parameters"></a>Paramètres  
 *dwTarget*  
 Indique la cible de la sortie du dump. Les valeurs possibles qui peuvent être combinés à l’aide de l’opération de bits OR ( **&#124;**) (opérateur), sont les suivantes :  
  
- AFX_STACK_DUMP_TARGET_TRACE envoie la sortie à l’aide de la [TRACE](#trace) (macro). La macro TRACE génère la sortie dans les versions debug uniquement. Il ne génère aucune sortie dans les versions release. En outre, la TRACE peut être redirigée vers d’autres cibles en dehors du débogueur.  
  
- AFX_STACK_DUMP_TARGET_DEFAULT envoie la sortie du dump à la cible par défaut. Pour une version debug, la sortie est envoyée à la macro TRACE. Dans une version Release, la sortie est envoyée dans le Presse-papiers.  
  
- AFX_STACK_DUMP_TARGET_CLIPBOARD envoie la sortie dans le Presse-papiers uniquement. Les données sont placées dans le Presse-papiers sous forme de texte brut en utilisant le format de Presse-papiers de CF_TEXT.  
  
- AFX_STACK_DUMP_TARGET_BOTH envoie en sortie dans le Presse-papiers et à la macro TRACE, simultanément.  
  
- AFX_STACK_DUMP_TARGET_ODS envoie la sortie directement dans le débogueur au moyen de la fonction Win32 `OutputDebugString()`. Cette option génère la sortie du débogueur dans les versions debug et versions release lorsqu’un débogueur est attaché au processus. AFX_STACK_DUMP_TARGET_ODS atteint toujours le débogueur (s’il est attaché) et ne peut pas être redirigé.  
  
### <a name="remarks"></a>Notes  
 L’exemple ci-dessous indique une ligne unique de la sortie générée par l’appel `AfxDumpStack` à partir d’un gestionnaire de bouton dans une application de la boîte de dialogue MFC :  
  
 `=== begin AfxDumpStack output ===`  
  
 `00427D55: DUMP2\DEBUG\DUMP2.EXE! void AfxDumpStack(unsigned long) + 181 bytes`  
  
 `0040160B: DUMP2\DEBUG\DUMP2.EXE! void CDump2Dlg::OnClipboard(void) + 14 bytes`  
  
 `0044F884: DUMP2\DEBUG\DUMP2.EXE! int _AfxDispatchCmdMsg(class CCmdTarget *,`  
  
 `unsigned int,int,void ( CCmdTarget::*)(void),void *,unsigned int,struct AFX_CMDHANDLE`  
  
 `0044FF7B: DUMP2\DEBUG\DUMP2.EXE! virtual int CCmdTarget::OnCmdMsg(unsigned`  
  
 `int,int,void *,struct AFX_CMDHANDLERINFO *) + 626 bytes`  
  
 `00450C71: DUMP2\DEBUG\DUMP2.EXE! virtual int CDialog::OnCmdMsg(unsigned`  
  
 `int,int,void *,struct AFX_CMDHANDLERINFO *) + 36 bytes`  
  
 `00455B27: DUMP2\DEBUG\DUMP2.EXE! virtual int CWnd::OnCommand(unsigned`  
  
 `int,long) + 312 bytes`  
  
 `00454D3D: DUMP2\DEBUG\DUMP2.EXE! virtual int CWnd::OnWndMsg(unsigned`  
  
 `int,unsigned int,long,long *) + 83 bytes`  
  
 `00454CC0: DUMP2\DEBUG\DUMP2.EXE! virtual long CWnd::WindowProc(unsigned`  
  
 `int,unsigned int,long) + 46 bytes`  
  
 `004528D9: DUMP2\DEBUG\DUMP2.EXE! long AfxCallWndProc(class CWnd *,struct`  
  
 `HWND__ *,unsigned int,unsigned int,long) + 237 bytes`  
  
 `00452D34: DUMP2\DEBUG\DUMP2.EXE! long AfxWndProc(struct HWND__ *,unsigned`  
  
 `int,unsigned int,long) + 129 bytes`  
  
 `BFF73663: WINDOWS\SYSTEM\KERNEL32.DLL! ThunkConnect32 + 2148 bytes`  
  
 `BFF928E0: WINDOWS\SYSTEM\KERNEL32.DLL! UTUnRegister + 2492 bytes`  
  
 `=== end AfxDumpStack() output ===`  
  
 Chaque ligne dans la sortie ci-dessus indique l’adresse du dernier appel de fonction, le nom de chemin d’accès complet du module qui contient l’appel de fonction et que le prototype de fonction appelée. Si l’appel de fonction sur la pile ne se produit pas à l’adresse exacte de la fonction, un décalage d’octets est indiqué.  
  
 Par exemple, le tableau suivant décrit la première ligne de la sortie ci-dessus :  
  
|Sortie|Description|  
|------------|-----------------|  
|`00427D55:`|L’adresse de retour du dernier appel de fonction.|  
|`DUMP2\DEBUG\DUMP2.EXE!`|Le nom de chemin d’accès complet du module qui contient l’appel de fonction.|  
|`void AfxDumpStack(unsigned long)`|Le prototype de fonction est appelée.|  
|`+ 181 bytes`|Le décalage en octets à partir de l’adresse du prototype de fonction (dans ce cas, `void AfxDumpStack(unsigned long)`) à l’adresse de retour (dans ce cas, `00427D55`).|  
  
 `AfxDumpStack` est disponible dans les versions debug ou non Debug des bibliothèques MFC ; Toutefois, la fonction est toujours liée de manière statique, même lorsque votre fichier exécutable utilise les MFC dans une DLL partagée. Dans les implémentations de la bibliothèque partagée, la fonction se trouve dans le MFCS42. Bibliothèque LIB (et ses variantes).  
  
 Pour utiliser cette fonction avec succès :  
  
-   Le fichier IMAGEHLP. DLL doit être sur votre chemin d’accès. Si vous n’avez pas cette DLL, la fonction affiche un message d’erreur. Consultez [bibliothèque d’aide Image](http://msdn.microsoft.com/library/windows/desktop/ms680321) pour plus d’informations sur l’ensemble de la fonction fournie par IMAGEHLP.  
  
-   Les modules qui ont des frames sur la pile doivent inclure les informations de débogage. Si elles ne contiennent pas les informations de débogage, la fonction va générer une trace de pile, mais la trace sera moins détaillée.  
### <a name="requirements"></a>Configuration requise  
 **En-tête :** afx.h 

##  <a name="afxenablememoryleakdump"></a>  AfxEnableMemoryLeakDump  
 Active ou désactive le dump de fuite de mémoire dans le destructeur AFX_DEBUG_STATE.  
  
```  
BOOL AFXAPI AfxEnableMemoryLeakDump(BOOL bDump);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *bDump*  
 TRUE indique que le dump de fuite de mémoire est activé ; FALSE indique que le dump de fuite de mémoire est désactivé.  
  
### <a name="return-value"></a>Valeur de retour  
 La valeur précédente pour cet indicateur.  
  
### <a name="remarks"></a>Notes  
 Quand une application décharge la bibliothèque MFC, cette bibliothèque recherche les fuites de mémoire. À ce stade, les fuites de mémoire sont transmis à l’utilisateur via la **déboguer** fenêtre de [!INCLUDE[vsprvs](../../assembler/masm/includes/vsprvs_md.md)].  
  
 Si votre application charge une autre bibliothèque avant la bibliothèque MFC, certaines allocations de mémoire dans cette bibliothèque sont considérées incorrectement comme des fuites de mémoire. Les fausses fuites de mémoire peuvent provoquer la fermeture lente de votre application car la bibliothèque MFC les signale. Dans ce cas, utilisez `AfxEnableMemoryLeakDump` pour désactiver l’image des fuites de mémoire.  
  
> [!NOTE]
>  Si vous utilisez cette méthode pour désactiver l’image des fuites de mémoire, vous ne recevez pas d’indication des fuites de mémoire valides dans votre application. Vous devez utiliser cette méthode seulement si vous êtes certain que le rapport sur les fuites de mémoire contient des fausses fuites de mémoire.  

### <a name="requirements"></a>Configuration requise  
 **En-tête :** afx.h 

##  <a name="afxenablememorytracking"></a>  AfxEnableMemoryTracking  
 Mémoire de diagnostic de suivi est normalement activée dans la version Debug des MFC.  
  
```   
BOOL AfxEnableMemoryTracking(BOOL bTrack); 
```  
  
### <a name="parameters"></a>Paramètres  
 *bTrack*  
 La valeur TRUE active sur l’utilisation de la mémoire ; FALSE le désactive.  
  
### <a name="return-value"></a>Valeur de retour  
 Le paramètre précédent de l’indicateur de suivi-enable.  
  
### <a name="remarks"></a>Notes  
 Cette fonction permet de désactiver le suivi des modifications sur les sections de votre code que vous connaissez sont allouer les blocs correctement.  
  
 Pour plus d’informations sur `AfxEnableMemoryTracking`, consultez [débogage des Applications MFC](/visualstudio/debugger/mfc-debugging-techniques).  
  
> [!NOTE]
>  Cette fonction fonctionne uniquement dans la version Debug des MFC.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_Utilities#24](../../mfc/codesnippet/cpp/diagnostic-services_12.cpp)]  
  
### <a name="requirements"></a>Configuration requise  
 **En-tête :** afx.h 

##  <a name="afxismemoryblock"></a>  AfxIsMemoryBlock  
 Teste une adresse mémoire pour vous assurer qu’il représente un bloc de mémoire actuellement actifs qui a été alloué par la version de diagnostic de **nouveau**.  
  
```   
BOOL AfxIsMemoryBlock(
    const void* p,  
    UINT nBytes,  
    LONG* plRequestNumber = NULL); 
```  
  
### <a name="parameters"></a>Paramètres  
 *p*  
 Pointe vers le bloc de mémoire à tester.  
  
 *nBytes*  
 Contient la longueur du bloc de mémoire en octets.  
  
 *plRequestNumber*  
 Pointe vers un **long** entier qui est remplie avec le numéro de séquence du bloc de mémoire d’allocation, ou zéro si elle ne représente pas un bloc de mémoire actuellement actifs.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si le bloc de mémoire est alloué actuellement et la longueur est correcte. Sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Il vérifie également la taille spécifiée par rapport à la taille allouée d’origine. Si la fonction retourne différente de zéro, le numéro de séquence d’allocation est retourné dans *plRequestNumber*. Ce nombre représente l’ordre dans lequel le bloc a été alloué par rapport à tous les autres **nouveau** allocations.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_Utilities#27](../../mfc/codesnippet/cpp/diagnostic-services_13.cpp)]  
  
### <a name="requirements"></a>Configuration requise  
 **En-tête :** afx.h 

##  <a name="afxisvalidaddress"></a>  AfxIsValidAddress  
 Tests de n’importe quelle adresse de mémoire pour vous assurer qu’elle est contenue entièrement dans l’espace de mémoire du programme.  
  
```   
BOOL AfxIsValidAddress(
    const void* lp,  
    UINT nBytes,  
    BOOL bReadWrite = TRUE); 
```  
  
### <a name="parameters"></a>Paramètres  
 *LP*  
 Pointe vers l’adresse de la mémoire doit être testée.  
  
 *nBytes*  
 Contient le nombre d’octets de mémoire doit être testée.  
  
 *bReadWrite*  
 Spécifie si la mémoire est à la fois pour la lecture et l’écriture (TRUE) ou simplement de la lecture (FALSE).  
  
### <a name="return-value"></a>Valeur de retour  
 Dans les versions debug, différent de zéro si le bloc de la mémoire spécifiée est contenue entièrement dans l’espace de mémoire du programme ; Sinon, 0.  
  
 Dans les versions non debug, différent de zéro si *lp* n’est pas NULL ; sinon, 0.  
  
### <a name="remarks"></a>Notes  
 L’adresse n’est pas limitée aux blocs alloués par **nouveau**.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_Utilities#28](../../mfc/codesnippet/cpp/diagnostic-services_14.cpp)]  
  
### <a name="requirements"></a>Configuration requise  
 **En-tête :** afx.h 

##  <a name="afxisvalidstring"></a>  AfxIsValidString  
 Utilisez cette fonction pour déterminer si un pointeur vers une chaîne est valid.  
  
```   
BOOL  AfxIsValidString(
    LPCSTR lpsz,  
    int nLength = -1); 
```  
  
### <a name="parameters"></a>Paramètres  
 *lpsz*  
 Le pointeur à tester.  
  
 *nLength*  
 Spécifie la longueur de la chaîne à tester, en octets. La valeur -1 indique que la chaîne se terminant par null.  
  
### <a name="return-value"></a>Valeur de retour  
 Dans les versions debug, différent de zéro si le pointeur spécifié pointe vers une chaîne de la taille spécifiée ; Sinon, 0.  
  
 Dans les versions non debug, différent de zéro si *lpsz* n’est pas NULL ; sinon, 0.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_Utilities#29](../../mfc/codesnippet/cpp/diagnostic-services_15.cpp)]  

### <a name="requirements"></a>Configuration requise  
 **En-tête :** afx.h 

##  <a name="afxsetallochook"></a>  AfxSetAllocHook  
 Définit un raccordement qui permet l’appel de la fonction spécifiée avant que chaque bloc de mémoire est allouée.  
  
```   
AFX_ALLOC_HOOK AfxSetAllocHook(AFX_ALLOC_HOOK pfnAllocHook); 
```  
  
### <a name="parameters"></a>Paramètres  
 *pfnAllocHook*  
 Spécifie le nom de la fonction à appeler. Consultez la section Notes pour le prototype d’une fonction d’allocation.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si vous souhaitez autoriser l’allocation ; Sinon, 0.  
  
### <a name="remarks"></a>Notes  
 L’allocateur de mémoire de débogage Microsoft Foundation Class Library peut appeler une fonction de raccordement définie par l’utilisateur pour permettre à l’utilisateur pour surveiller une allocation de mémoire et de contrôler si l’allocation est autorisée. Fonctions de raccordement d’allocation sont prototypées comme suit :  
  
 **BOOL sur AllocHook (size_t** `nSize` **, BOOL** `bObject` **, LONG** `lRequestNumber` **) ;**  
  
 *nSize*  
 La taille de l’allocation de mémoire proposée.  
  
 *bLe*  
 TRUE si l’allocation est pour un `CObject`-objet dérivée ; sinon, FALSE.  
  
 *lRequestNumber*  
 Numéro de séquence de l’allocation de mémoire.  
  
 Notez que la convention d’appel de AFXAPI implique que l’appelé doit supprimer les paramètres de la pile.  

### <a name="requirements"></a>Configuration requise  
 **En-tête :** afx.h 

##  <a name="afxdoforallclasses"></a>  AfxDoForAllClasses  
 Appelle la fonction de l’itération spécifiée pour tous sérialisables `CObject`-classes dérivées de l’espace de mémoire de l’application.  
  
```   
void  
AFXAPI AfxDoForAllClasses(
    void (* pfn)(const CRuntimeClass* pClass, void* pContext),  
    void* pContext); 
```  
  
### <a name="parameters"></a>Paramètres  
 *pfn*  
 Pointe vers une fonction de l’itération soit appelé pour chaque classe. Les arguments de fonction sont un pointeur vers un `CRuntimeClass` objet et un pointeur void vers les données supplémentaires que l’appelant fournit à la fonction.  
  
 *pContext*  
 Points de données facultatif qui peut fournir l’appelant à la fonction de l’itération. Ce pointeur peut être NULL.  
  
### <a name="remarks"></a>Notes  
 Sérialisable `CObject`-classes dérivées sont des classes dérivées à l’aide de la macro DECLARE_SERIAL. Le pointeur passé à `AfxDoForAllClasses` dans *pContext* est passé à la fonction de l’itération spécifiée chaque fois qu’elle est appelée.  
  
> [!NOTE]
>  Cette fonction fonctionne uniquement dans la version Debug des MFC.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCCollections#113](../../mfc/codesnippet/cpp/diagnostic-services_16.cpp)]  
  
 [!code-cpp[NVC_MFCCollections#114](../../mfc/codesnippet/cpp/diagnostic-services_17.cpp)]  
  
### <a name="requirements"></a>Configuration requise  
 **En-tête :** afx.h 

##  <a name="afxdoforallobjects"></a>  AfxDoForAllObjects  
 Exécute la fonction de l’itération spécifiée pour tous les objets dérivés de `CObject` qui ont été alloués avec **nouveau**.  
  
```   
void AfxDoForAllObjects(
    void (* pfn)(CObject* pObject, void* pContext),  
    void* pContext); 
```  
  
### <a name="parameters"></a>Paramètres  
 *pfn*  
 Pointe vers une fonction de l’itération à exécuter pour chaque objet. Les arguments de fonction sont un pointeur vers un `CObject` et un pointeur void vers les données supplémentaires que l’appelant fournit à la fonction.  
  
 *pContext*  
 Points de données facultatif qui peut fournir l’appelant à la fonction de l’itération. Ce pointeur peut être NULL.  
  
### <a name="remarks"></a>Notes  
 Pile, global, ou des objets incorporés ne sont pas énumérées. Le pointeur passé à `AfxDoForAllObjects` dans *pContext* est passé à la fonction de l’itération spécifiée chaque fois qu’elle est appelée.  
  
> [!NOTE]
>  Cette fonction fonctionne uniquement dans la version Debug des MFC.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCCollections#115](../../mfc/codesnippet/cpp/diagnostic-services_18.cpp)]  
  
 [!code-cpp[NVC_MFCCollections#116](../../mfc/codesnippet/cpp/diagnostic-services_19.cpp)]  
  
## <a name="see-also"></a>Voir aussi  
 [Macros et objet Globals](../../mfc/reference/mfc-macros-and-globals.md)