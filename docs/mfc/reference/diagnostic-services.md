---
title: Services de diagnostic
ms.date: 11/04/2016
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
ms.openlocfilehash: 4cf3f53d1e238218b4eb892dc92e3c823dcc1296
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2020
ms.locfileid: "79421400"
---
# <a name="diagnostic-services"></a>Services de diagnostic

La bibliothèque Microsoft Foundation Class fournit de nombreux services de diagnostic qui simplifient le débogage de vos programmes. Elle propose notamment des macros et des fonctions globales qui vous permettent d’effectuer le suivi des allocations mémoire de votre programme, de vider le contenu des objets au moment de l’exécution et d’afficher des messages de débogage au moment de l’exécution. Les macros et les fonctions globales pour les services de diagnostic sont regroupées dans les catégories suivantes :

- Macros de diagnostic général

- Fonctions et variables de diagnostic général

- Fonctions de diagnostic d’objet

Ces macros et fonctions sont disponibles pour toutes les classes dérivées de `CObject` dans les versions Debug et Release de MFC. Toutefois, toutes les DEBUG_NEW à l’exception de et de VERIFY ne font rien dans la version Release.

Dans la bibliothèque Debug, tous les blocs de mémoire alloués sont entourés d’une série d’« octets de protection ». Si ces octets sont perturbés par une écriture en mémoire non contrôlée, les routines de diagnostic peuvent signaler un problème. Si vous incluez la ligne :

[!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/cpp/diagnostic-services_1.cpp)]

dans votre fichier d’implémentation, tous les appels à **new** stockent le nom de fichier et le numéro de ligne où l’allocation de mémoire a eu lieu. La fonction [CMemoryState::DumpAllObjectsSince](cmemorystate-structure.md#dumpallobjectssince) affiche ces informations supplémentaires, ce qui vous permet d’identifier les fuites de mémoire. Pour plus d’informations sur la sortie de diagnostic, consultez également la classe [CDumpContext](../../mfc/reference/cdumpcontext-class.md) .

La bibliothèque Runtime C prend également en charge un ensemble de fonctions de diagnostic que vous pouvez utiliser pour déboguer vos applications. Pour plus d’informations, consultez [Routines de débogage](../../c-runtime-library/debug-routines.md) dans la Référence de la bibliothèque runtime.

### <a name="mfc-general-diagnostic-macros"></a>Macros de diagnostic général MFC

|||
|-|-|
|[ASSERT](#assert)|Affiche un message et interrompt le programme si l’expression spécifiée donne la valeur FALSE dans la version Debug de la bibliothèque.|
|[ASSERT_KINDOF](#assert_kindof)|Vérifie qu’un objet est un objet de la classe spécifiée ou d’une classe dérivée de la classe spécifiée.|
|[ASSERT_VALID](#assert_valid)|Teste la validité interne d’un objet en appelant sa fonction membre `AssertValid` ; généralement substituée à partir de `CObject`.|
|[DEBUG_NEW](#debug_new)|Fournit un nom de fichier et un numéro de ligne pour toutes les allocations d’objets en mode débogage, pour faciliter la recherche des fuites de mémoire.|
|[DEBUG_ONLY](#debug_only)|Semblable à ASSERT, mais ne teste pas la valeur de l’expression. Utile pour le code qui doit s’exécuter uniquement en mode débogage.|
|[Vérifiez et ENSURE_VALID](#ensure)|Utilisez pour valider l’exactitude des données.|
|[THIS_FILE](#this_file)|Se développe sur le nom du fichier en cours de compilation.|
|[TRACE](#trace)|Fournit des fonctionnalités semblables à `printf`dans la version Debug de la bibliothèque.|
|[VERIFY](#verify)|Semblable à ASSERT, mais évalue l’expression dans la versions Release et Debug de la bibliothèque.|

### <a name="mfc-general-diagnostic-variables-and-functions"></a>Fonctions et variables de diagnostic général MFC

|||
|-|-|
|[afxDump](#afxdump)|Variable globale qui envoie des informations [CDumpContext](../../mfc/reference/cdumpcontext-class.md) à la fenêtre de sortie du débogueur ou au terminal de débogage.|
|[afxMemDF](#afxmemdf)|Variable globale qui contrôle le comportement de l’allocateur de mémoire de débogage.|
|[AfxCheckError](#afxcheckerror)|Variable globale qui sert à tester le SCODE passé pour voir s’il s’agit d’une erreur et, si c’est le cas, génère l’erreur appropriée.|
|[AfxCheckMemory](#afxcheckmemory)|Vérifie l’intégrité de toute la mémoire allouée actuellement.|
|[AfxDebugBreak](#afxdebugbreak)|Provoque un arrêt de l’exécution.|
|[AfxDump](#cdumpcontext_in_mfc)|En cas d’appel dans le débogueur, vide l’état d’un objet pendant le débogage.|
|[AfxDump](#afxdump)|Fonction interne qui vide l’état d’un objet pendant le débogage.|
|[AfxDumpStack](#afxdumpstack)|Générer une image de la pile actuelle. Cette fonction est toujours liée de manière statique.|
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

### <a name="mfc-compilation-macros"></a>Macros de compilation MFC

|||
|-|-|
|[_AFX_SECURE_NO_WARNINGS](#afx_secure_no_warnings)|Supprime les avertissements du compilateur pour l’utilisation de fonctions MFC déconseillées.|

## <a name="afx_secure_no_warnings"></a>_AFX_SECURE_NO_WARNINGS

Supprime les avertissements du compilateur pour l’utilisation de fonctions MFC déconseillées.

### <a name="syntax"></a>Syntaxe

```
_AFX_SECURE_NO_WARNINGS
```

### <a name="example"></a>Exemple

Cet exemple de code provoque un avertissement du compilateur si _AFX_SECURE_NO_WARNINGS n’ont pas été définis.

```cpp
// define this before including any afx files in *pch.h* (*stdafx.h* in Visual Studio 2017 and earlier)
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

Appelez cette fonction pour provoquer un arrêt (à l’emplacement de l’appel à `AfxDebugBreak`) dans l’exécution de la version Debug de votre application MFC.

### <a name="syntax"></a>Syntaxe

```
void AfxDebugBreak( );
```

### <a name="remarks"></a>Notes

`AfxDebugBreak` n’a aucun effet dans les versions Release d’une application MFC et doit être supprimé. Cette fonction doit être utilisée uniquement dans les applications MFC. Utilisez la version de l’API Win32, `DebugBreak`, pour provoquer une rupture dans des applications non-MFC.

### <a name="requirements"></a>Spécifications

**En-tête :** afxver_. h

##  <a name="assert"></a>  ASSERT

Évalue son argument.

```
ASSERT(booleanExpression)
```

### <a name="parameters"></a>Paramètres

*booleanExpression*<br/>
Spécifie une expression (y compris des valeurs de pointeur) qui prend une valeur différente de zéro ou égale à 0.

### <a name="remarks"></a>Notes

Si le résultat est 0, la macro imprime un message de diagnostic et abandonne le programme. Si la condition est différente de zéro, elle ne fait rien.

Le message de diagnostic se présente sous la forme

`assertion failed in file <name> in line <num>`

où *Name* est le nom du fichier source et *num* est le numéro de ligne de l’assertion qui a échoué dans le fichier source.

Dans la version finale de MFC, Assert n’évalue pas l’expression et n’interrompt donc pas le programme. Si l’expression doit être évaluée quel que soit l’environnement, utilisez la macro VERIFY à la place de la méthode Assert.

> [!NOTE]
>  Cette fonction est uniquement disponible dans la version Debug de MFC.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_Utilities#44](../../mfc/codesnippet/cpp/diagnostic-services_2.cpp)]

### <a name="requirements"></a>Spécifications

**En-tête :** afx.h

##  <a name="assert_kindof"></a>  ASSERT_KINDOF

Cette macro déclare que l’objet pointé est un objet de la classe spécifiée ou est un objet d’une classe dérivée de la classe spécifiée.

```
ASSERT_KINDOF(classname, pobject)
```

### <a name="parameters"></a>Paramètres

*classname*<br/>
Nom d’une classe dérivée de `CObject`.

*pObject*<br/>
Pointeur vers un objet de classe.

### <a name="remarks"></a>Notes

Le paramètre *pObject* doit être un pointeur vers un objet et peut être **const**. L’objet vers lequel pointe la classe doit prendre en charge `CObject` informations de classe au moment de l’exécution. Par exemple, pour vous assurer que `pDocument` est un pointeur vers un objet de la classe `CMyDoc`, ou de l’un de ses dérivés, vous pouvez coder :

[!code-cpp[NVC_MFCDocView#194](../../mfc/codesnippet/cpp/diagnostic-services_3.cpp)]

L’utilisation de la macro `ASSERT_KINDOF` est exactement identique au codage :

[!code-cpp[NVC_MFCDocView#195](../../mfc/codesnippet/cpp/diagnostic-services_4.cpp)]

Cette fonction fonctionne uniquement pour les classes déclarées avec la macro [DECLARE_DYNAMIC] (Run-Time-Object-Model-services. MD # declare_dynamic ou [DECLARE_SERIAL](run-time-object-model-services.md#declare_serial) .

> [!NOTE]
>  Cette fonction est uniquement disponible dans la version Debug de MFC.

### <a name="requirements"></a>Spécifications

**En-tête :** afx.h

##  <a name="assert_valid"></a>  ASSERT_VALID

Utilisez pour tester vos hypothèses sur la validité de l’état interne d’un objet.

```
ASSERT_VALID(pObject)
```

### <a name="parameters"></a>Paramètres

*pObject*<br/>
Spécifie un objet d’une classe dérivée de `CObject` qui a une version de substitution de la fonction membre `AssertValid`.

### <a name="remarks"></a>Notes

ASSERT_VALID appelle la fonction membre `AssertValid` de l’objet passé comme argument.

Dans la version finale de MFC, ASSERT_VALID ne fait rien. Dans la version de débogage, il valide le pointeur, vérifie par rapport à la valeur NULL et appelle les propres fonctions membres de l’objet `AssertValid`. Si l’un de ces tests échoue, un message d’alerte s’affiche de la même manière que l’instruction [Assert](#assert).

> [!NOTE]
>  Cette fonction est uniquement disponible dans la version Debug de MFC.

Pour plus d’informations et d’exemples, consultez [débogage des applications MFC](/visualstudio/debugger/mfc-debugging-techniques).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCObjectSample#19](../../mfc/codesnippet/cpp/diagnostic-services_5.cpp)]

### <a name="requirements"></a>Spécifications

**En-tête :** afx.h

##  <a name="debug_new"></a>  DEBUG_NEW

Aide à la recherche de fuites de mémoire.

```
#define  new DEBUG_NEW
```

### <a name="remarks"></a>Notes

Dans votre programme, vous pouvez utiliser DEBUG_NEW partout où vous utiliseriez généralement l’opérateur **New** pour allouer le stockage du tas.

En mode débogage (lorsque le symbole **_DEBUG** est défini), DEBUG_NEW effectue le suivi du nom de fichier et du numéro de ligne pour chaque objet qu’il alloue. Ensuite, lorsque vous utilisez la fonction membre [CMemoryState ::D umpallobjectssince](cmemorystate-structure.md#dumpallobjectssince) , chaque objet alloué avec DEBUG_NEW est affiché avec le nom de fichier et le numéro de ligne où il a été alloué.

Pour utiliser DEBUG_NEW, insérez la directive suivante dans vos fichiers sources :

[!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/cpp/diagnostic-services_1.cpp)]

Une fois que vous avez inséré cette directive, le préprocesseur insère DEBUG_NEW partout où vous utilisez **New**, et MFC fait le reste. Quand vous compilez une version Release de votre programme, DEBUG_NEW se résout en une **nouvelle** opération simple, et les informations de nom de fichier et de numéro de ligne ne sont pas générées.

> [!NOTE]
>  Dans les versions précédentes de MFC (4,1 et versions antérieures), vous deviez placer l’instruction `#define` après toutes les instructions qui ont appelé les macros IMPLEMENT_DYNCREATE ou IMPLEMENT_SERIAL. Cela n'est plus nécessaire.

### <a name="requirements"></a>Spécifications

**En-tête :** afx.h

##  <a name="debug_only"></a>  DEBUG_ONLY

En mode débogage (lorsque le symbole **_DEBUG** est défini), DEBUG_ONLY évalue son argument.

```
DEBUG_ONLY(expression)
```

### <a name="remarks"></a>Notes

Dans une version Release, DEBUG_ONLY n’évalue pas son argument. Cela est utile lorsque vous avez du code qui doit être exécuté uniquement dans les versions Debug.

La macro DEBUG_ONLY équivaut à l' *expression* environnante avec `#ifdef _DEBUG` et `#endif`.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_Utilities#32](../../mfc/codesnippet/cpp/diagnostic-services_6.cpp)]

### <a name="requirements"></a>Spécifications

**En-tête :** afx.h

### <a name="ensure"></a>Vérifiez et ENSURE_VALID

Utilisez pour valider l’exactitude des données.

### <a name="syntax"></a>Syntaxe

```
ENSURE(  booleanExpression )
ENSURE_VALID( booleanExpression  )
```

### <a name="parameters"></a>Paramètres

*booleanExpression*<br/>
Spécifie une expression booléenne à tester.

### <a name="remarks"></a>Notes

L’objectif de ces macros est d’améliorer la validation des paramètres. Les macros empêchent la poursuite du traitement des paramètres incorrects dans votre code. Contrairement aux macros Assert, les macros s’ASSUREnt de lever une exception en plus de générer une assertion.

Les macros se comportent de deux façons, en fonction de la configuration du projet. Les macros appellent Assert, puis lèvent une exception si l’assertion échoue. Ainsi, dans les configurations Debug (autrement dit, où _DEBUG est défini), les macros produisent une assertion et une exception dans les configurations Release, les macros produisent uniquement l’exception (Assert n’évalue pas l’expression dans les configurations Release).

La macro ENSURE_ARG agit comme la macro garantir.

ENSURE_VALID appelle la macro ASSERT_VALID (qui a un effet uniquement dans les versions Debug). En outre, ENSURE_VALID lève une exception si le pointeur a la valeur NULL. Le test NULL est exécuté à la fois dans les configurations Debug et Release.

Si l’un de ces tests échoue, un message d’alerte s’affiche de la même manière que l’instruction Assert. La macro lève une exception d’argument non valide si nécessaire.
### <a name="requirements"></a>Spécifications

**En-tête :** afx.h

## <a name="this_file"></a>THIS_FILE

Se développe sur le nom du fichier en cours de compilation.

### <a name="syntax"></a>Syntaxe

```
THIS_FILE
```

### <a name="remarks"></a>Notes

Les informations sont utilisées par les macros Assert et VERIFY. L’Assistant Application et les assistants code placent la macro dans les fichiers de code source qu’elle crée.

### <a name="example"></a>Exemple

```cpp
#ifdef _DEBUG
#undef THIS_FILE
static char THIS_FILE[] = __FILE__;
#endif

// __FILE__ is one of the six predefined ANSI C macros that the
// compiler recognizes.
```

### <a name="requirements"></a>Spécifications

**En-tête :** afx.h

##  <a name="trace"></a>  TRACE

Envoie la chaîne spécifiée au débogueur de l’application actuelle.

```
TRACE(exp)
TRACE(DWORD  category,  UINT  level, LPCSTR lpszFormat, ...)
```

### <a name="remarks"></a>Notes

Pour obtenir une description de TRACE, consultez [ATLTRACE2](../../atl/reference/debugging-and-error-reporting-macros.md#atltrace2) . TRACE et ATLTRACE2 ont le même comportement.

Dans la version Debug des MFC, cette macro envoie la chaîne spécifiée au débogueur de l’application actuelle. Dans une version Release, cette macro se compile en Nothing (aucun code n’est généré).

Pour plus d’informations, consultez [débogage des applications MFC](/visualstudio/debugger/mfc-debugging-techniques).

### <a name="requirements"></a>Spécifications

**En-tête :** afx.h

##  <a name="verify"></a>  VERIFY

Dans la version Debug de MFC, évalue son argument.

```
VERIFY(booleanExpression)
```

### <a name="parameters"></a>Paramètres

*booleanExpression*<br/>
Spécifie une expression (y compris des valeurs de pointeur) qui prend une valeur différente de zéro ou égale à 0.

### <a name="remarks"></a>Notes

Si le résultat est 0, la macro imprime un message de diagnostic et interrompt le programme. Si la condition est différente de zéro, elle ne fait rien.

Le message de diagnostic se présente sous la forme

`assertion failed in file <name> in line <num>`

où *Name* est le nom du fichier source et *num* est le numéro de ligne de l’assertion qui a échoué dans le fichier source.

Dans la version finale de MFC, VERIFY évalue l’expression, mais n’imprime pas ou n’interrompt pas le programme. Par exemple, si l’expression est un appel de fonction, l’appel est effectué.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#198](../../mfc/codesnippet/cpp/diagnostic-services_7.cpp)]

### <a name="requirements"></a>Spécifications

**En-tête :** afx.h

##  <a name="cdumpcontext_in_mfc"></a>afxDump (CDumpContext dans MFC)

Fournit une fonctionnalité de vidage d’objet de base dans votre application.

```
CDumpContext  afxDump;
```

### <a name="remarks"></a>Notes

`afxDump` est un objet [CDumpContext](../../mfc/reference/cdumpcontext-class.md) prédéfini qui vous permet d’envoyer des informations de `CDumpContext` à la fenêtre sortie du débogueur ou à un terminal de débogage. En général, vous fournissez `afxDump` en tant que paramètre pour `CObject::Dump`.

Sous Windows NT et toutes les versions de Windows, `afxDump` sortie est envoyée à la fenêtre de débogage de C++ sortie de Visual quand vous déboguez votre application.

Cette variable est définie uniquement dans la version Debug de MFC. Pour plus d’informations sur les `afxDump`, consultez [débogage des applications MFC](/visualstudio/debugger/mfc-debugging-techniques).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_Utilities#23](../../mfc/codesnippet/cpp/diagnostic-services_8.cpp)]

### <a name="requirements"></a>Spécifications

**En-tête :** afx.h

## <a name="afxdump"></a>AfxDump (interne)

Fonction interne que MFC utilise pour vider l’état d’un objet pendant le débogage.

### <a name="syntax"></a>Syntaxe

```
void AfxDump(const CObject* pOb);
```

### <a name="parameters"></a>Paramètres

*pOb*<br/>
Pointeur vers un objet d’une classe dérivée de `CObject`.

### <a name="remarks"></a>Notes

`AfxDump` appelle la fonction membre `Dump` d’un objet et envoie les informations à l’emplacement spécifié par la variable `afxDump`. `AfxDump` est disponible uniquement dans la version Debug de MFC.

Votre code de programme ne doit pas appeler `AfxDump`, mais doit plutôt appeler la fonction membre `Dump` de l’objet approprié.

### <a name="requirements"></a>Spécifications

**En-tête :** afx.h

##  <a name="afxmemdf"></a>  afxMemDF

Cette variable est accessible à partir d’un débogueur ou de votre programme, et vous permet de paramétrer les diagnostics d’allocation.

```
int  afxMemDF;
```

### <a name="remarks"></a>Notes

`afxMemDF` peut avoir les valeurs suivantes, comme spécifié par l’énumération `afxMemDF`:

- `allocMemDF` active l’allocateur de débogage (paramètre par défaut dans la bibliothèque de débogage).

- `delayFreeMemDF` retarde la libération de la mémoire. Alors que votre programme libère un bloc de mémoire, l’allocateur ne retourne pas cette mémoire au système d’exploitation sous-jacent. Cela placera la contrainte de mémoire maximale sur votre programme.

- `checkAlwaysMemDF` appelle `AfxCheckMemory` chaque fois que la mémoire est allouée ou libérée. Cela ralentit considérablement les allocations et les désallocations de mémoire.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_Utilities#30](../../mfc/codesnippet/cpp/diagnostic-services_9.cpp)]

### <a name="requirements"></a>Spécifications

**En-tête :** afx.h

##  <a name="afxcheckerror"></a>  AfxCheckError

Cette fonction teste l’SCODE passé pour voir s’il s’agit d’une erreur.

```
void AFXAPI AfxCheckError(SCODE sc);
throw CMemoryException*
throw COleException*
```

### <a name="remarks"></a>Notes

S’il s’agit d’une erreur, la fonction lève une exception. Si le SCODE passé est E_OUTOFMEMORY, la fonction lève une [CMemoryException](../../mfc/reference/cmemoryexception-class.md) en appelant [AfxThrowMemoryException](exception-processing.md#afxthrowmemoryexception). Dans le cas contraire, la fonction lève une [COleException](../../mfc/reference/coleexception-class.md) en appelant [AfxThrowOleException](exception-processing.md#afxthrowoleexception).

Cette fonction peut être utilisée pour vérifier les valeurs de retour des appels aux fonctions OLE dans votre application. En testant la valeur de retour avec cette fonction dans votre application, vous pouvez réagir correctement aux conditions d’erreur avec une quantité minimale de code.

> [!NOTE]
>  Cette fonction a le même effet dans les versions Debug et non Debug.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCOleContainer#33](../../mfc/codesnippet/cpp/diagnostic-services_10.cpp)]

### <a name="requirements"></a>Spécifications

**En-tête :** afx.h

##  <a name="afxcheckmemory"></a>  AfxCheckMemory

Cette fonction valide le pool de mémoire libre et imprime les messages d’erreur selon les besoins.

```
BOOL  AfxCheckMemory();
```

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro si aucune erreur de mémoire n’est détectée ; Sinon, 0.

### <a name="remarks"></a>Notes

Si la fonction ne détecte aucune altération de la mémoire, elle n’affiche rien.

Tous les blocs de mémoire actuellement alloués sur le tas sont vérifiés, y compris ceux qui sont alloués par les **nouveaux** , mais pas ceux alloués par les appels directs aux allocateurs de mémoire sous-jacents, tels que la fonction **malloc** ou la fonction Windows `GlobalAlloc`. Si un bloc est endommagé, un message est affiché dans la sortie du débogueur.

Si vous incluez la ligne

[!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/cpp/diagnostic-services_1.cpp)]

dans un module de programme, les appels suivants à `AfxCheckMemory` affichent le nom de fichier et le numéro de ligne où la mémoire a été allouée.

> [!NOTE]
>  Si votre module contient une ou plusieurs implémentations de classes sérialisables, vous devez placer la ligne de `#define` après le dernier appel de macro IMPLEMENT_SERIAL.

Cette fonction fonctionne uniquement dans la version Debug de MFC.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCObjectSample#26](../../mfc/codesnippet/cpp/diagnostic-services_11.cpp)]

### <a name="requirements"></a>Spécifications

**En-tête :** afx.h

##  <a name="afxdump"></a>AfxDump (MFC)

Appelez cette fonction dans le débogueur pour vider l’état d’un objet pendant le débogage.

```
void AfxDump(const CObject* pOb);
```

### <a name="parameters"></a>Paramètres

*pOb*<br/>
Pointeur vers un objet d’une classe dérivée de `CObject`.

### <a name="remarks"></a>Notes

`AfxDump` appelle la fonction membre `Dump` d’un objet et envoie les informations à l’emplacement spécifié par la variable `afxDump`. `AfxDump` est disponible uniquement dans la version Debug de MFC.

Votre code de programme ne doit pas appeler `AfxDump`, mais doit plutôt appeler la fonction membre `Dump` de l’objet approprié.

### <a name="requirements"></a>Spécifications

**En-tête :** afx.h

##  <a name="afxdumpstack"></a>  AfxDumpStack

Cette fonction globale peut être utilisée pour générer une image de la pile actuelle.

```
void AFXAPI AfxDumpStack(DWORD dwTarget = AFX_STACK_DUMP_TARGET_DEFAULT);
```

### <a name="parameters"></a>Paramètres

*dwTarget*<br/>
Indique la cible de la sortie du dump. Les valeurs possibles, qui peuvent être combinées à l’aide de **&#124;** l’opérateur de bits or (), sont les suivantes :

- AFX_STACK_DUMP_TARGET_TRACE envoie la sortie au moyen de la macro [trace](#trace) . La macro TRACE génère une sortie uniquement dans les versions Debug. elle ne génère aucune sortie dans les versions release. En outre, la TRACE peut être redirigée vers d’autres cibles en dehors du débogueur.

- AFX_STACK_DUMP_TARGET_DEFAULT envoie la sortie du dump à la cible par défaut. Pour une version Debug, la sortie est envoyée à la macro TRACE. Dans une version Release, la sortie est insérée dans le presse-papiers.

- AFX_STACK_DUMP_TARGET_CLIPBOARD envoie la sortie dans le presse-papiers uniquement. Les données sont placées dans le presse-papiers sous forme de texte brut à l’aide du format CF_TEXT presse-papiers.

- AFX_STACK_DUMP_TARGET_BOTH envoie simultanément la sortie dans le presse-papiers et la macro TRACE.

- AFX_STACK_DUMP_TARGET_ODS envoie la sortie directement au débogueur au moyen de la fonction Win32 `OutputDebugString()`. Cette option génère la sortie du débogueur dans les versions Debug et Release quand un débogueur est attaché au processus. AFX_STACK_DUMP_TARGET_ODS atteint toujours le débogueur (s’il est attaché) et ne peut pas être redirigé.

### <a name="remarks"></a>Notes

L’exemple ci-dessous reflète une ligne unique de la sortie générée par l’appel de `AfxDumpStack` à partir d’un gestionnaire de bouton dans une application de boîte de dialogue MFC :

```Output
=== begin AfxDumpStack output ===
00427D55: DUMP2\DEBUG\DUMP2.EXE! void AfxDumpStack(unsigned long) + 181 bytes
0040160B: DUMP2\DEBUG\DUMP2.EXE! void CDump2Dlg::OnClipboard(void) + 14 bytes
0044F884: DUMP2\DEBUG\DUMP2.EXE! int _AfxDispatchCmdMsg(class CCmdTarget *,
unsigned int,int,void ( CCmdTarget::*)(void),void *,unsigned int,struct
AFX_CMDHANDLE
0044FF7B: DUMP2\DEBUG\DUMP2.EXE! virtual int CCmdTarget::OnCmdMsg(unsigned
int,int,void *,struct AFX_CMDHANDLERINFO *) + 626 bytes
00450C71: DUMP2\DEBUG\DUMP2.EXE! virtual int CDialog::OnCmdMsg(unsigned
int,int,void *,struct AFX_CMDHANDLERINFO *) + 36 bytes
00455B27: DUMP2\DEBUG\DUMP2.EXE! virtual int CWnd::OnCommand(unsigned
int,long) + 312 bytes
00454D3D: DUMP2\DEBUG\DUMP2.EXE! virtual int CWnd::OnWndMsg(unsigned
int,unsigned int,long,long *) + 83 bytes
00454CC0: DUMP2\DEBUG\DUMP2.EXE! virtual long CWnd::WindowProc(unsigned
int,unsigned int,long) + 46 bytes
004528D9: DUMP2\DEBUG\DUMP2.EXE! long AfxCallWndProc(class CWnd *,struct
HWND__ *,unsigned int,unsigned int,long) + 237 bytes
00452D34: DUMP2\DEBUG\DUMP2.EXE! long AfxWndProc(struct HWND__ *,unsigned
int,unsigned int,long) + 129 bytes
BFF73663: WINDOWS\SYSTEM\KERNEL32.DLL! ThunkConnect32 + 2148 bytes
BFF928E0: WINDOWS\SYSTEM\KERNEL32.DLL! UTUnRegister + 2492 bytes
=== end AfxDumpStack() output ===
```

Chaque ligne de la sortie ci-dessus indique l’adresse du dernier appel de fonction, le nom de chemin d’accès complet du module qui contient l’appel de fonction et le prototype de fonction appelé. Si l’appel de fonction sur la pile ne se produit pas à l’adresse exacte de la fonction, un décalage d’octets est affiché.

Par exemple, le tableau suivant décrit la première ligne de la sortie ci-dessus :

|Output|Description|
|------------|-----------------|
|`00427D55:`|Adresse de retour du dernier appel de fonction.|
|`DUMP2\DEBUG\DUMP2.EXE!`|Nom de chemin d’accès complet du module qui contient l’appel de fonction.|
|`void AfxDumpStack(unsigned long)`|Le prototype de fonction appelé.|
|`+ 181 bytes`|Offset, en octets, à partir de l’adresse du prototype de fonction (dans ce cas, `void AfxDumpStack(unsigned long)`) à l’adresse de retour (dans le cas présent, `00427D55`).|

`AfxDumpStack` est disponible dans les versions Debug et non Debug des bibliothèques MFC. Toutefois, la fonction est toujours liée de manière statique, même lorsque votre fichier exécutable utilise MFC dans une DLL partagée. Dans les implémentations de bibliothèque partagée, la fonction se trouve dans le MFCS42. Bibliothèque LIB (et ses variantes).

Pour utiliser correctement cette fonction :

- Fichier IMAGEHLP. La DLL doit se trouver sur votre chemin d’accès. Si vous n’avez pas cette DLL, la fonction affichera un message d’erreur. Pour plus d’informations sur l’ensemble de fonctions fourni par IMAGEHLP, consultez [bibliothèque d’aide](/windows/win32/Debug/image-help-library) sur les images.

- Les modules qui ont des frames sur la pile doivent inclure des informations de débogage. S’ils ne contiennent pas d’informations de débogage, la fonction génère toujours une trace de la pile, mais la trace sera moins détaillée.
  ### <a name="requirements"></a>Spécifications

**En-tête :** afx.h

##  <a name="afxenablememoryleakdump"></a>AfxEnableMemoryLeakDump

Active et désactive le vidage des fuites de mémoire dans le destructeur AFX_DEBUG_STATE.

```
BOOL AFXAPI AfxEnableMemoryLeakDump(BOOL bDump);
```

### <a name="parameters"></a>Paramètres

*bDump*<br/>
dans TRUE indique que le vidage des fuites de mémoire est activé ; FALSe indique que le vidage des fuites de mémoire est désactivé.

### <a name="return-value"></a>Valeur de retour

La valeur précédente pour cet indicateur.

### <a name="remarks"></a>Notes

Quand une application décharge la bibliothèque MFC, cette bibliothèque recherche les fuites de mémoire. À ce stade, toutes les fuites de mémoire sont signalées à l’utilisateur via la fenêtre de **débogage** de Visual Studio.

Si votre application charge une autre bibliothèque avant la bibliothèque MFC, certaines allocations de mémoire dans cette bibliothèque sont considérées incorrectement comme des fuites de mémoire. Les fausses fuites de mémoire peuvent provoquer la fermeture lente de votre application car la bibliothèque MFC les signale. Dans ce cas, utilisez `AfxEnableMemoryLeakDump` pour désactiver l’image des fuites de mémoire.

> [!NOTE]
>  Si vous utilisez cette méthode pour désactiver l’image des fuites de mémoire, vous ne recevez pas d’indication des fuites de mémoire valides dans votre application. Vous devez utiliser cette méthode seulement si vous êtes certain que le rapport sur les fuites de mémoire contient des fausses fuites de mémoire.

### <a name="requirements"></a>Spécifications

**En-tête :** afx.h

##  <a name="afxenablememorytracking"></a>  AfxEnableMemoryTracking

Le suivi de la mémoire de diagnostic est normalement activé dans la version de débogage de MFC.

```
BOOL AfxEnableMemoryTracking(BOOL bTrack);
```

### <a name="parameters"></a>Paramètres

*bTrack*<br/>
L’affectation de la valeur TRUE active le suivi de la mémoire. FALSe le désactive.

### <a name="return-value"></a>Valeur de retour

Paramètre précédent de l’indicateur Tracking-Enable.

### <a name="remarks"></a>Notes

Utilisez cette fonction pour désactiver le suivi des sections de votre code dont vous savez que les blocs sont correctement alloués.

Pour plus d’informations sur les `AfxEnableMemoryTracking`, consultez [débogage des applications MFC](/visualstudio/debugger/mfc-debugging-techniques).

> [!NOTE]
>  Cette fonction fonctionne uniquement dans la version Debug de MFC.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_Utilities#24](../../mfc/codesnippet/cpp/diagnostic-services_12.cpp)]

### <a name="requirements"></a>Spécifications

**En-tête :** afx.h

##  <a name="afxismemoryblock"></a>  AfxIsMemoryBlock

Teste une adresse mémoire pour s’assurer qu’elle représente un bloc de mémoire actuellement actif qui a été alloué par la version de diagnostic de **New**.

```
BOOL AfxIsMemoryBlock(
    const void* p,
    UINT nBytes,
    LONG* plRequestNumber = NULL);
```

### <a name="parameters"></a>Paramètres

*p*<br/>
Pointe vers le bloc de mémoire à tester.

*nBytes*<br/>
Contient la longueur du bloc de mémoire en octets.

*plRequestNumber*<br/>
Pointe vers un entier **long** qui sera rempli avec le numéro de séquence d’allocation du bloc de mémoire, ou zéro s’il ne représente pas un bloc de mémoire actuellement actif.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si le bloc de mémoire est actuellement alloué et que la longueur est correcte ; Sinon, 0.

### <a name="remarks"></a>Notes

Elle vérifie également la taille spécifiée par rapport à la taille allouée d’origine. Si la fonction retourne une valeur différente de zéro, le numéro de séquence d’allocation est retourné dans *plRequestNumber*. Ce nombre représente l’ordre dans lequel le bloc a été alloué par rapport à toutes les **nouvelles** allocations.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_Utilities#27](../../mfc/codesnippet/cpp/diagnostic-services_13.cpp)]

### <a name="requirements"></a>Spécifications

**En-tête :** afx.h

##  <a name="afxisvalidaddress"></a>  AfxIsValidAddress

Teste toute adresse mémoire pour s’assurer qu’elle est entièrement contenue dans l’espace mémoire du programme.

```
BOOL AfxIsValidAddress(
    const void* lp,
    UINT nBytes,
    BOOL bReadWrite = TRUE);
```

### <a name="parameters"></a>Paramètres

*Aid*<br/>
Pointe vers l’adresse mémoire à tester.

*nBytes*<br/>
Contient le nombre d’octets de mémoire à tester.

*bReadWrite*<br/>
Spécifie si la mémoire est à la fois pour la lecture et l’écriture (TRUE) ou simplement pour la lecture (FALSe).

### <a name="return-value"></a>Valeur de retour

Dans les versions Debug, valeur différente de zéro si le bloc de mémoire spécifié est entièrement contenu dans l’espace mémoire du programme ; Sinon, 0.

Dans les versions sans débogage, valeur différente de zéro si *LP* n’est pas null ; Sinon, 0.

### <a name="remarks"></a>Notes

L’adresse n’est pas limitée aux blocs alloués par **New**.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_Utilities#28](../../mfc/codesnippet/cpp/diagnostic-services_14.cpp)]

### <a name="requirements"></a>Spécifications

**En-tête :** afx.h

##  <a name="afxisvalidstring"></a>  AfxIsValidString

Utilisez cette fonction pour déterminer si un pointeur vers une chaîne est valide.

```
BOOL  AfxIsValidString(
    LPCSTR lpsz,
    int nLength = -1);
```

### <a name="parameters"></a>Paramètres

*lpsz*<br/>
Pointeur à tester.

*nLength*<br/>
Spécifie la longueur de la chaîne à tester, en octets. La valeur-1 indique que la chaîne se termine par un caractère null.

### <a name="return-value"></a>Valeur de retour

Dans les versions Debug, valeur différente de zéro si le pointeur spécifié pointe vers une chaîne de la taille spécifiée ; Sinon, 0.

Dans les versions sans débogage, valeur différente de zéro si *lpsz* n’est pas null ; Sinon, 0.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_Utilities#29](../../mfc/codesnippet/cpp/diagnostic-services_15.cpp)]

### <a name="requirements"></a>Spécifications

**En-tête :** afx.h

##  <a name="afxsetallochook"></a>  AfxSetAllocHook

Définit un hook qui active l’appel de la fonction spécifiée avant que chaque bloc de mémoire ne soit alloué.

```
AFX_ALLOC_HOOK AfxSetAllocHook(AFX_ALLOC_HOOK pfnAllocHook);
```

### <a name="parameters"></a>Paramètres

*pfnAllocHook*<br/>
Spécifie le nom de la fonction à appeler. Consultez les notes pour le prototype d’une fonction d’allocation.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si vous souhaitez autoriser l’allocation ; Sinon, 0.

### <a name="remarks"></a>Notes

L’allocateur de mémoire de débogage bibliothèque MFC (Microsoft Foundation Class) peut appeler une fonction de raccordement définie par l’utilisateur pour permettre à l’utilisateur de surveiller une allocation de mémoire et contrôler si l’allocation est autorisée. Les fonctions de raccordement d’allocation sont prototypées comme suit :

**Bool AFXAPI AllocHook (size_t** `nSize` **, bool** `bObject` **, long** `lRequestNumber` **);**

*nSize*<br/>
Taille de l’allocation de mémoire proposée.

*bObject*<br/>
TRUE si l’allocation concerne un objet dérivé de `CObject`; Sinon, FALSe.

*lRequestNumber*<br/>
Numéro de séquence de l’allocation de mémoire.

Notez que la Convention d’appel AFXAPI implique que l’appelé doit supprimer les paramètres de la pile.

### <a name="requirements"></a>Spécifications

**En-tête :** afx.h

##  <a name="afxdoforallclasses"></a>  AfxDoForAllClasses

Appelle la fonction d’itération spécifiée pour toutes les classes sérialisables dérivées de `CObject`dans l’espace mémoire de l’application.

```
void
AFXAPI AfxDoForAllClasses(
    void (* pfn)(const CRuntimeClass* pClass, void* pContext),
    void* pContext);
```

### <a name="parameters"></a>Paramètres

*PFN*<br/>
Pointe vers une fonction d’itération à appeler pour chaque classe. Les arguments de fonction sont un pointeur vers un objet `CRuntimeClass` et un pointeur void vers des données supplémentaires que l’appelant fournit à la fonction.

*pContext*<br/>
Pointe vers des données facultatives que l’appelant peut fournir à la fonction d’itération. Ce pointeur peut avoir la valeur NULL.

### <a name="remarks"></a>Notes

Les classes dérivées de `CObject`sérialisables sont des classes dérivées à l’aide de la macro DECLARE_SERIAL. Le pointeur qui est passé à `AfxDoForAllClasses` dans *pContext* est passé à la fonction d’itération spécifiée chaque fois qu’il est appelé.

> [!NOTE]
>  Cette fonction fonctionne uniquement dans la version Debug de MFC.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#113](../../mfc/codesnippet/cpp/diagnostic-services_16.cpp)]

[!code-cpp[NVC_MFCCollections#114](../../mfc/codesnippet/cpp/diagnostic-services_17.cpp)]

### <a name="requirements"></a>Spécifications

**En-tête :** afx.h

##  <a name="afxdoforallobjects"></a>  AfxDoForAllObjects

Exécute la fonction d’itération spécifiée pour tous les objets dérivés de `CObject` qui ont été alloués avec **New**.

```
void AfxDoForAllObjects(
    void (* pfn)(CObject* pObject, void* pContext),
    void* pContext);
```

### <a name="parameters"></a>Paramètres

*PFN*<br/>
Pointe vers une fonction d’itération à exécuter pour chaque objet. Les arguments de fonction sont un pointeur vers une `CObject` et un pointeur void vers des données supplémentaires que l’appelant fournit à la fonction.

*pContext*<br/>
Pointe vers des données facultatives que l’appelant peut fournir à la fonction d’itération. Ce pointeur peut avoir la valeur NULL.

### <a name="remarks"></a>Notes

Les objets Stack, global ou incorporé ne sont pas énumérés. Le pointeur passé à `AfxDoForAllObjects` dans *pContext* est passé à la fonction d’itération spécifiée chaque fois qu’il est appelé.

> [!NOTE]
>  Cette fonction fonctionne uniquement dans la version Debug de MFC.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#115](../../mfc/codesnippet/cpp/diagnostic-services_18.cpp)]

[!code-cpp[NVC_MFCCollections#116](../../mfc/codesnippet/cpp/diagnostic-services_19.cpp)]

## <a name="see-also"></a>Voir aussi

[Macros et globales](mfc-macros-and-globals.md)<br/>
[CObject ::D UMP](cobject-class.md#dump)
