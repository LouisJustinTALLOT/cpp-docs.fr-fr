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
ms.openlocfilehash: 8db12a73d64641a52fea3056de8ab3180c9239b2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365793"
---
# <a name="diagnostic-services"></a>Services de diagnostic

La bibliothèque Microsoft Foundation Class fournit de nombreux services de diagnostic qui simplifient le débogage de vos programmes. Elle propose notamment des macros et des fonctions globales qui vous permettent d’effectuer le suivi des allocations mémoire de votre programme, de vider le contenu des objets au moment de l’exécution et d’afficher des messages de débogage au moment de l’exécution. Les macros et les fonctions globales pour les services de diagnostic sont regroupées dans les catégories suivantes :

- Macros de diagnostic général

- Fonctions et variables de diagnostic général

- Fonctions de diagnostic d’objet

Ces macros et fonctions sont disponibles pour toutes les classes dérivées de `CObject` dans les versions Debug et Release de MFC. Cependant, tous sauf DEBUG_NEW et VERIFY ne font rien dans la version Version Release.

Dans la bibliothèque Debug, tous les blocs de mémoire alloués sont entourés d’une série d’« octets de protection ». Si ces octets sont perturbés par une écriture en mémoire non contrôlée, les routines de diagnostic peuvent signaler un problème. Si vous incluez la ligne :

[!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/cpp/diagnostic-services_1.cpp)]

dans votre fichier de mise en œuvre, tous les appels vers **de nouveaux** stockeront le nom de fichier et le numéro de ligne où l’allocation de mémoire a eu lieu. La fonction [CMemoryState::DumpAllObjectsSince](cmemorystate-structure.md#dumpallobjectssince) affichera ces informations supplémentaires, vous permettant d’identifier les fuites de mémoire. Consultez également la classe [CDumpContext](../../mfc/reference/cdumpcontext-class.md) pour obtenir des informations supplémentaires sur la sortie diagnostique.

La bibliothèque Runtime C prend également en charge un ensemble de fonctions de diagnostic que vous pouvez utiliser pour déboguer vos applications. Pour plus d’informations, voir [Debug Routines](../../c-runtime-library/debug-routines.md) dans la référence de la bibliothèque Run-Time.

### <a name="mfc-general-diagnostic-macros"></a>Macros de diagnostic général MFC

|||
|-|-|
|[Affirmer](#assert)|Affiche un message et interrompt le programme si l’expression spécifiée donne la valeur FALSE dans la version Debug de la bibliothèque.|
|[ASSERT_KINDOF](#assert_kindof)|Vérifie qu’un objet est un objet de la classe spécifiée ou d’une classe dérivée de la classe spécifiée.|
|[ASSERT_VALID](#assert_valid)|Teste la validité interne d’un objet en appelant sa fonction membre `AssertValid` ; généralement substituée à partir de `CObject`.|
|[DEBUG_NEW](#debug_new)|Fournit un nom de fichier et un numéro de ligne pour toutes les allocations d’objets en mode débogage, pour faciliter la recherche des fuites de mémoire.|
|[DEBUG_ONLY](#debug_only)|Semblable à ASSERT, mais ne teste pas la valeur de l’expression. Utile pour le code qui doit s’exécuter uniquement en mode débogage.|
|[ENSURE et ENSURE_VALID](#ensure)|Utiliser pour valider la justesse des données.|
|[THIS_FILE](#this_file)|Élargit au nom du fichier qui est en cours de compilation.|
|[Trace](#trace)|Fournit des fonctionnalités semblables à `printf`dans la version Debug de la bibliothèque.|
|[Vérifier](#verify)|Semblable à ASSERT, mais évalue l’expression dans la versions Release et Debug de la bibliothèque.|

### <a name="mfc-general-diagnostic-variables-and-functions"></a>Fonctions et variables de diagnostic général MFC

|||
|-|-|
|[afxDump](#afxdump)|Variable globale qui envoie des informations [CDumpContext](../../mfc/reference/cdumpcontext-class.md) à la fenêtre de sortie de débbuggeur ou au terminal de débogé.|
|[afxMemDF](#afxmemdf)|Variable globale qui contrôle le comportement de l’allocateur de mémoire de débogage.|
|[AfxCheckError](#afxcheckerror)|Variable globale qui sert à tester le SCODE passé pour voir s’il s’agit d’une erreur et, si c’est le cas, génère l’erreur appropriée.|
|[AfxCheckMemory AfxCheckMemory](#afxcheckmemory)|Vérifie l’intégrité de toute la mémoire allouée actuellement.|
|[AfxDebugBreak](#afxdebugbreak)|Provoque une interruption d’exécution.|
|[afxDump](#cdumpcontext_in_mfc)|En cas d’appel dans le débogueur, vide l’état d’un objet pendant le débogage.|
|[afxDump](#afxdump)|Fonction interne qui décharge l’état d’un objet tout en débogage.|
|[AfxDumpStack](#afxdumpstack)|Génère une image de la pile actuelle. Cette fonction est toujours liée de manière statique.|
|[AfxEnableMemoryLeakDump](#afxenablememoryleakdump)|Active le vidage de fuite de mémoire.|
|[AfxEnableMemoryTracking AfxEnableMemoryTracking AfxEnableMemoryTracking Afx](#afxenablememorytracking)|Active et désactive le suivi de la mémoire.|
|[AfxIsMemoryBlock](#afxismemoryblock)|Vérifie qu’un bloc de mémoire a été alloué correctement.|
|[AfxIsValidAddress](#afxisvalidaddress)|Vérifie qu’une plage d’adresses mémoire est dans les limites du programme.|
|[AfxIsValidString](#afxisvalidstring)|Détermine si un pointeur vers une chaîne est valide.|
|[AfxSetAllocHook](#afxsetallochook)|Permet l’appel d’une fonction lors de chaque allocation de mémoire.|

### <a name="mfc-object-diagnostic-functions"></a>Fonctions de diagnostic d’objet MFC

|||
|-|-|
|[AfxDoForAllClasses](#afxdoforallclasses)|Exécute une fonction spécifiée sur toutes les classes dérivées de `CObject`qui prennent en charge la vérification du type au moment de l’exécution.|
|[AfxDoForAllObjects](#afxdoforallobjects)|Exécute une fonction spécifiée sur tous les objets dérivés de `CObject`qui ont été alloués avec **new**.|

### <a name="mfc-compilation-macros"></a>MFC Compilation Macros

|||
|-|-|
|[_AFX_SECURE_NO_WARNINGS](#afx_secure_no_warnings)|Supprime les avertissements de compilateur pour l’utilisation des fonctions MFC dépréciées.|

## <a name="_afx_secure_no_warnings"></a><a name="afx_secure_no_warnings"></a>_AFX_SECURE_NO_WARNINGS

Supprime les avertissements de compilateur pour l’utilisation des fonctions MFC dépréciées.

### <a name="syntax"></a>Syntaxe

```
_AFX_SECURE_NO_WARNINGS
```

### <a name="example"></a>Exemple

Cet échantillon de code provoquerait un avertissement de compilateur si _AFX_SECURE_NO_WARNINGS n’étaient pas définis.

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

## <a name="afxdebugbreak"></a><a name="afxdebugbreak"></a>AfxDebugBreak

Appelez cette fonction pour provoquer une pause (à l’emplacement de l’appel à `AfxDebugBreak`) dans l’exécution de la version de débogé de votre application MFC.

### <a name="syntax"></a>Syntaxe

```
void AfxDebugBreak( );
```

### <a name="remarks"></a>Notes

`AfxDebugBreak`n’a aucun effet dans les versions de version d’une application MFC et doit être supprimé. Cette fonction ne doit être utilisée que dans les applications MFC. Utilisez la version API `DebugBreak`Win32, pour provoquer une pause dans les applications non-MFC.

### <a name="requirements"></a>Spécifications

**En-tête:** afxver_.h

## <a name="assert"></a><a name="assert"></a>Affirmer

Évalue son argument.

```
ASSERT(booleanExpression)
```

### <a name="parameters"></a>Paramètres

*booleanExpression*<br/>
Spécifie une expression (y compris les valeurs pointeurs) qui s’évalue à nonzero ou 0.

### <a name="remarks"></a>Notes

Si le résultat est de 0, la macro imprime un message diagnostique et avorte le programme. Si la condition n’est pas zéro, elle ne fait rien.

Le message de diagnostic se présente sous la forme

`assertion failed in file <name> in line <num>`

où le *nom* est le nom du fichier source, et *num* est le numéro de ligne de l’affirmation qui a échoué dans le fichier source.

Dans la version Release de MFC, ASSERT n’évalue pas l’expression et n’interrompt donc pas le programme. Si l’expression doit être évaluée quel que soit l’environnement, utilisez la macro VERIFY à la place de ASSERT.

> [!NOTE]
> Cette fonction n’est disponible que dans la version Debug de MFC.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_Utilities#44](../../mfc/codesnippet/cpp/diagnostic-services_2.cpp)]

### <a name="requirements"></a>Spécifications

**En-tête:** afx.h

## <a name="assert_kindof"></a><a name="assert_kindof"></a>ASSERT_KINDOF

Cette macro affirme que l’objet pointé vers le haut est un objet de la classe spécifiée, ou est un objet d’une classe dérivée de la classe spécifiée.

```
ASSERT_KINDOF(classname, pobject)
```

### <a name="parameters"></a>Paramètres

*Classname*<br/>
Le nom `CObject`d’une classe dérivée.

*pobject*<br/>
Un pointeur à un objet de classe.

### <a name="remarks"></a>Notes

Le paramètre *pobject* doit être un pointeur à un objet et peut être **const**. L’objet indiqué et la `CObject` classe doivent prendre en charge les informations de classe de temps d’exécution. Par exemple, pour `pDocument` vous assurer qu’il `CMyDoc` s’agit d’un pointeur d’un objet de la classe ou de l’un de ses dérivés, vous pouvez coder :

[!code-cpp[NVC_MFCDocView#194](../../mfc/codesnippet/cpp/diagnostic-services_3.cpp)]

L’utilisation de la `ASSERT_KINDOF` macro est exactement la même que le codage:

[!code-cpp[NVC_MFCDocView#195](../../mfc/codesnippet/cpp/diagnostic-services_4.cpp)]

Cette fonction ne fonctionne que pour les classes déclarées avec le [DECLARE_DYNAMIC] (run-time-object-model-services.md-declare_dynamic ou [DECLARE_SERIAL](run-time-object-model-services.md#declare_serial) macro.

> [!NOTE]
> Cette fonction n’est disponible que dans la version Debug de MFC.

### <a name="requirements"></a>Spécifications

**En-tête:** afx.h

## <a name="assert_valid"></a><a name="assert_valid"></a>ASSERT_VALID

Utilisez pour tester vos hypothèses sur la validité de l’état interne d’un objet.

```
ASSERT_VALID(pObject)
```

### <a name="parameters"></a>Paramètres

*pObject*<br/>
Spécifie un objet `CObject` d’une classe dérivée `AssertValid` de qui a une version primordiale de la fonction membre.

### <a name="remarks"></a>Notes

ASSERT_VALID appelle la `AssertValid` fonction membre de l’objet adopté comme son argument.

Dans la version Version Version de MFC, ASSERT_VALID ne fait rien. Dans la version Debug, il valide le pointeur, vérifie contre `AssertValid` NULL, et appelle les fonctions de membre de l’objet. Si l’un de ces tests échoue, un message d’alerte est affiché de la même manière que [ASSERT](#assert).

> [!NOTE]
> Cette fonction n’est disponible que dans la version Debug de MFC.

Pour plus d’informations et d’exemples, voir [Debugging MFC Applications](/visualstudio/debugger/mfc-debugging-techniques).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCObjectSample#19](../../mfc/codesnippet/cpp/diagnostic-services_5.cpp)]

### <a name="requirements"></a>Spécifications

**En-tête:** afx.h

## <a name="debug_new"></a><a name="debug_new"></a>DEBUG_NEW

Aide à trouver des fuites de mémoire.

```
#define  new DEBUG_NEW
```

### <a name="remarks"></a>Notes

Vous pouvez utiliser DEBUG_NEW partout dans votre programme que vous utiliseriez habituellement le **nouvel** opérateur pour allouer le stockage de tas.

En mode débogé (lorsque le symbole **_DEBUG** est défini), DEBUG_NEW garde une trace du nom de fichier et du numéro de ligne pour chaque objet qu’il attribue. Ensuite, lorsque vous utilisez la fonction [membre CMemoryState::DumpAllObjectsSince,](cmemorystate-structure.md#dumpallobjectssince) chaque objet attribué avec DEBUG_NEW est affiché avec le nom de fichier et le numéro de ligne où il a été attribué.

Pour utiliser DEBUG_NEW, insérez la directive suivante dans vos fichiers sources :

[!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/cpp/diagnostic-services_1.cpp)]

Une fois que vous insérez cette directive, le préprocesseur insère DEBUG_NEW partout où vous utilisez **de nouvelles**, et MFC fait le reste. Lorsque vous compilez une version de version de votre programme, DEBUG_NEW se résout à une **nouvelle** opération simple, et les informations sur le nom de fichier et le numéro de ligne ne sont pas générées.

> [!NOTE]
> Dans les versions précédentes de MFC (4.1 `#define` et plus tôt) vous aviez besoin de mettre la déclaration après toutes les déclarations qui ont appelé le IMPLEMENT_DYNCREATE ou IMPLEMENT_SERIAL macros. Cela n'est plus nécessaire.

### <a name="requirements"></a>Spécifications

**En-tête:** afx.h

## <a name="debug_only"></a><a name="debug_only"></a>DEBUG_ONLY

En mode débogé (lorsque le symbole **_DEBUG** est défini), DEBUG_ONLY évalue son argument.

```
DEBUG_ONLY(expression)
```

### <a name="remarks"></a>Notes

Dans une version, DEBUG_ONLY n’évalue pas son argument. Ceci est utile lorsque vous avez du code qui ne doit être exécuté que dans les constructions de débogé.

La macro DEBUG_ONLY est équivalente à `#ifdef _DEBUG` `#endif` *l’expression* environnante avec et .

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_Utilities#32](../../mfc/codesnippet/cpp/diagnostic-services_6.cpp)]

### <a name="requirements"></a>Spécifications

**En-tête:** afx.h

### <a name="ensure-and-ensure_valid"></a><a name="ensure"></a>ENSURE et ENSURE_VALID

Utiliser pour valider la justesse des données.

### <a name="syntax"></a>Syntaxe

```
ENSURE(  booleanExpression )
ENSURE_VALID( booleanExpression  )
```

### <a name="parameters"></a>Paramètres

*booleanExpression*<br/>
Spécifie une expression boolean à tester.

### <a name="remarks"></a>Notes

Le but de ces macros est d’améliorer la validation des paramètres. Les macros empêchent le traitement ultérieur des paramètres incorrects dans votre code. Contrairement aux macros ASSERT, les macros ENSURE jettent une exception en plus de générer une affirmation.

Les macros se comportent de deux manières, selon la configuration du projet. Les macros appellent ASSERT et jettent ensuite une exception si l’affirmation échoue. Ainsi, dans les configurations Debug (c’est-à-dire, lorsque _DEBUG est définie), les macros produisent une affirmation et une exception tandis que dans les configurations de libération, les macros ne produisent que l’exception (ASSERT n’évalue pas l’expression dans les configurations de libération).

Le macro ENSURE_ARG agit comme la macro ENSURE.

ENSURE_VALID appelle le ASSERT_VALID macro (qui n’a d’effet que dans les constructions Debug). En outre, ENSURE_VALID lance une exception si le pointeur est NULL. Le test NULL est effectué dans les configurations Debug et Release.

Si l’un de ces tests échoue, un message d’alerte s’affiche de la même manière que ASSERT. La macro jette une exception d’argument invalide si nécessaire.

### <a name="requirements"></a>Spécifications

**En-tête:** afx.h

## <a name="this_file"></a><a name="this_file"></a>THIS_FILE

Élargit au nom du fichier qui est en cours de compilation.

### <a name="syntax"></a>Syntaxe

```
THIS_FILE
```

### <a name="remarks"></a>Notes

L’information est utilisée par les macros ASSERT et VERIFY. L’Assistant d’Application et les assistants de code placent la macro dans les fichiers de code source qu’ils créent.

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

**En-tête:** afx.h

## <a name="trace"></a><a name="trace"></a>Trace

Envoie la chaîne spécifiée au débbuggeur de l’application actuelle.

```
TRACE(exp)
TRACE(DWORD  category,  UINT  level, LPCSTR lpszFormat, ...)
```

### <a name="remarks"></a>Notes

Voir [ATLTRACE2](../../atl/reference/debugging-and-error-reporting-macros.md#atltrace2) pour une description de TRACE. TRACE et ATLTRACE2 ont le même comportement.

Dans la version de débogé de MFC, cette macro envoie la chaîne spécifiée au débbugger de l’application actuelle. Dans une version, cette macro compile à rien (aucun code n’est généré du tout).

Pour plus d’informations, voir [Debugging MFC Applications](/visualstudio/debugger/mfc-debugging-techniques).

### <a name="requirements"></a>Spécifications

**En-tête:** afx.h

## <a name="verify"></a><a name="verify"></a>Vérifier

Dans la version Debug de MFC, évalue son argument.

```
VERIFY(booleanExpression)
```

### <a name="parameters"></a>Paramètres

*booleanExpression*<br/>
Spécifie une expression (y compris les valeurs pointeurs) qui s’évalue à nonzero ou 0.

### <a name="remarks"></a>Notes

Si le résultat est de 0, la macro imprime un message diagnostique et arrête le programme. Si la condition n’est pas zéro, elle ne fait rien.

Le message de diagnostic se présente sous la forme

`assertion failed in file <name> in line <num>`

où le *nom* est le nom du fichier source et *num* est le numéro de ligne de l’affirmation qui a échoué dans le fichier source.

Dans la version Release de MFC, VERIFY évalue l’expression mais n’imprime ni n’interrompt le programme. Par exemple, si l’expression est un appel de fonction, l’appel sera fait.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#198](../../mfc/codesnippet/cpp/diagnostic-services_7.cpp)]

### <a name="requirements"></a>Spécifications

**En-tête:** afx.h

## <a name="afxdump-cdumpcontext-in-mfc"></a><a name="cdumpcontext_in_mfc"></a>afxDump (CDumpContext dans MFC)

Fournit une capacité de déchargement d’objets de base dans votre application.

```
CDumpContext  afxDump;
```

### <a name="remarks"></a>Notes

`afxDump`est un objet [CDumpContext](../../mfc/reference/cdumpcontext-class.md) prédéfini `CDumpContext` qui vous permet d’envoyer des informations à la fenêtre de sortie de débbugger ou à un terminal de débbug. Typiquement, vous `afxDump` fournissez `CObject::Dump`comme un paramètre à .

Sous Windows NT et toutes `afxDump` les versions de Windows, la sortie est envoyée à la fenêtre Output-Debug de Visual CMD lorsque vous débbug votre application.

Cette variable n’est définie que dans la version Debug de MFC. Pour plus `afxDump`d’informations sur , voir [Debugging MFC Applications](/visualstudio/debugger/mfc-debugging-techniques).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_Utilities#23](../../mfc/codesnippet/cpp/diagnostic-services_8.cpp)]

### <a name="requirements"></a>Spécifications

**En-tête:** afx.h

## <a name="afxdump-internal"></a><a name="afxdump"></a>AfxDump (Interne)

Fonction interne que MFC utilise pour vider l’état d’un objet tout en débogage.

### <a name="syntax"></a>Syntaxe

```
void AfxDump(const CObject* pOb);
```

### <a name="parameters"></a>Paramètres

*Pob*<br/>
Un pointeur à un objet `CObject`d’une classe dérivée de .

### <a name="remarks"></a>Notes

`AfxDump`appelle la fonction `Dump` membre d’un objet et envoie `afxDump` les informations à l’emplacement spécifié par la variable. `AfxDump`n’est disponible que dans la version Debug de MFC.

Votre code de `AfxDump`programme ne doit `Dump` pas appeler, mais devrait plutôt appeler la fonction du membre de l’objet approprié.

### <a name="requirements"></a>Spécifications

**En-tête:** afx.h

## <a name="afxmemdf"></a><a name="afxmemdf"></a>afxMemDF

Cette variable est accessible à partir d’un débbuggeur ou de votre programme et vous permet d’accorder des diagnostics d’allocation.

```
int  afxMemDF;
```

### <a name="remarks"></a>Notes

`afxMemDF`peuvent avoir les valeurs suivantes telles `afxMemDF`que spécifiées par l’énumération :

- `allocMemDF`Active l’alloueur de débogage (paramètre par défaut dans la bibliothèque Debug).

- `delayFreeMemDF`Retarde la libération de la mémoire. Bien que votre programme libère un bloc de mémoire, l’allocateur ne retourne pas cette mémoire au système d’exploitation sous-jacent. Cela imposera un maximum de stress de mémoire sur votre programme.

- `checkAlwaysMemDF`Appels `AfxCheckMemory` chaque fois que la mémoire est allouée ou libérée. Cela ralentira considérablement les allocations de mémoire et les allocations.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_Utilities#30](../../mfc/codesnippet/cpp/diagnostic-services_9.cpp)]

### <a name="requirements"></a>Spécifications

**En-tête:** afx.h

## <a name="afxcheckerror"></a><a name="afxcheckerror"></a>AfxCheckError

Cette fonction teste le SCODE passé pour voir s’il s’agit d’une erreur.

```
void AFXAPI AfxCheckError(SCODE sc);
throw CMemoryException*
throw COleException*
```

### <a name="remarks"></a>Notes

S’il s’agit d’une erreur, la fonction fait une exception. Si le SCODE passé est E_OUTOFMEMORY, la fonction jette un [CMemoryException](../../mfc/reference/cmemoryexception-class.md) en appelant [AfxThrowMemoryException](exception-processing.md#afxthrowmemoryexception). Sinon, la fonction lance un [COleException](../../mfc/reference/coleexception-class.md) en appelant [AfxThrowOleException](exception-processing.md#afxthrowoleexception).

Cette fonction peut être utilisée pour vérifier les valeurs de retour des appels vers les fonctions OLE dans votre application. En testant la valeur de retour avec cette fonction dans votre application, vous pouvez réagir correctement aux conditions d’erreur avec une quantité minimale de code.

> [!NOTE]
> Cette fonction a le même effet dans les constructions de débogé et de non-débbug.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCOleContainer#33](../../mfc/codesnippet/cpp/diagnostic-services_10.cpp)]

### <a name="requirements"></a>Spécifications

**En-tête:** afx.h

## <a name="afxcheckmemory"></a><a name="afxcheckmemory"></a>AfxCheckMemory AfxCheckMemory

Cette fonction valide le pool de mémoire gratuit et imprime les messages d’erreur au besoin.

```
BOOL  AfxCheckMemory();
```

### <a name="return-value"></a>Valeur de retour

Nonzero si aucune erreur de mémoire; sinon 0.

### <a name="remarks"></a>Notes

Si la fonction ne détecte aucune corruption de mémoire, elle n’imprime rien.

Tous les blocs de mémoire actuellement attribués sur le tas sont vérifiés, y compris ceux alloués par **les nouveaux** mais pas ceux alloués par des appels directs aux allocateurs de mémoire sous-jacents, tels que la fonction **malloc** ou la `GlobalAlloc` fonction Windows. Si un bloc est trouvé pour être corrompu, un message est imprimé à la sortie de débogénaire.

Si vous incluez la ligne

[!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/cpp/diagnostic-services_1.cpp)]

dans un module de programme, puis les appels suivants pour `AfxCheckMemory` afficher le nom de fichier et le numéro de ligne où la mémoire a été attribuée.

> [!NOTE]
> Si votre module contient une ou plusieurs implémentations `#define` de classes sérialisables, alors vous devez mettre la ligne après le dernier IMPLEMENT_SERIAL macro appel.

Cette fonction ne fonctionne que dans la version Debug de MFC.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCObjectSample#26](../../mfc/codesnippet/cpp/diagnostic-services_11.cpp)]

### <a name="requirements"></a>Spécifications

**En-tête:** afx.h

## <a name="afxdump-mfc"></a><a name="afxdump"></a>AfxDump (MFC)

Appelez cette fonction tandis que dans le débogage pour vider l’état d’un objet tout en débogage.

```
void AfxDump(const CObject* pOb);
```

### <a name="parameters"></a>Paramètres

*Pob*<br/>
Un pointeur à un objet `CObject`d’une classe dérivée de .

### <a name="remarks"></a>Notes

`AfxDump`appelle la fonction `Dump` membre d’un objet et envoie `afxDump` les informations à l’emplacement spécifié par la variable. `AfxDump`n’est disponible que dans la version Debug de MFC.

Votre code de `AfxDump`programme ne doit `Dump` pas appeler, mais devrait plutôt appeler la fonction du membre de l’objet approprié.

### <a name="requirements"></a>Spécifications

**En-tête:** afx.h

## <a name="afxdumpstack"></a><a name="afxdumpstack"></a>AfxDumpStack

Cette fonction globale peut être utilisée pour générer une image de la pile actuelle.

```
void AFXAPI AfxDumpStack(DWORD dwTarget = AFX_STACK_DUMP_TARGET_DEFAULT);
```

### <a name="parameters"></a>Paramètres

*dwTarget dwTarget*<br/>
Indique la cible de la sortie du dépotoir. Les valeurs possibles, qui peuvent être combinées à l’aide de l’opérateur bitwise-OR ( **&#124;), **sont les suivantes :

- AFX_STACK_DUMP_TARGET_TRACE envoie la sortie au moyen de la macro [TRACE.](#trace) La macro TRACE génère la production dans les constructions de débogé seulement; il ne génère aucune sortie dans les versions. En outre, TRACE peut être redirigé vers d’autres cibles en plus du débbugger.

- AFX_STACK_DUMP_TARGET_DEFAULT envoie la sortie de décharge à la cible par défaut. Pour une construction de débaillement, la production va à la macro TRACE. Dans une version, la sortie va au Clipboard.

- AFX_STACK_DUMP_TARGET_CLIPBOARD envoie la sortie au Clipboard seulement. Les données sont placées sur le Clipboard sous forme de texte simple en utilisant le format CF_TEXT Clipboard.

- AFX_STACK_DUMP_TARGET_BOTH envoie la sortie au Clipboard et à la macro TRACE, simultanément.

- AFX_STACK_DUMP_TARGET_ODS envoie la sortie directement au débagénaire au moyen `OutputDebugString()`de la fonction Win32 . Cette option générera la sortie de débbugger dans les deux debug et la version construit quand un débbugger est attaché au processus. AFX_STACK_DUMP_TARGET_ODS atteint toujours le débbuggeur (s’il est attaché) et ne peut pas être redirigé.

### <a name="remarks"></a>Notes

L’exemple ci-dessous reflète une seule `AfxDumpStack` ligne de sortie générée par l’appel d’un gestionnaire de bouton dans une application de dialogue MFC :

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

Chaque ligne dans la sortie ci-dessus indique l’adresse du dernier appel de fonction, le nom complet du mode du module qui contient l’appel de fonction, et le prototype de fonction appelé. Si l’appel de fonction sur la pile ne se produit pas à l’adresse exacte de la fonction, un décalage des octets est montré.

Par exemple, le tableau suivant décrit la première ligne de la sortie ci-dessus :

|Output|Description|
|------------|-----------------|
|`00427D55:`|L’adresse de retour du dernier appel de fonction.|
|`DUMP2\DEBUG\DUMP2.EXE!`|Le nom complet du mode de parcours du module qui contient l’appel de fonction.|
|`void AfxDumpStack(unsigned long)`|Le prototype de fonction appelé.|
|`+ 181 bytes`|Le décalage dans les octets de l’adresse `void AfxDumpStack(unsigned long)`du prototype de fonction (dans `00427D55`ce cas, ) à l’adresse de retour (dans ce cas, ).|

`AfxDumpStack`est disponible en versions débbug et non débagé des bibliothèques MFC; cependant, la fonction est toujours liée statiquement, même lorsque votre fichier exécutable utilise MFC dans un DLL partagé. Dans les implémentations de bibliothèques partagées, la fonction se trouve dans le MFCS42. Bibliothèque LIB (et ses variantes).

Pour utiliser cette fonction avec succès :

- Le fichier IMAGEHLP. DLL doit être sur votre chemin. Si vous n’avez pas ce DLL, la fonction affichera un message d’erreur. Voir [Image Help Library](/windows/win32/Debug/image-help-library) pour plus d’informations sur l’ensemble de fonction fourni par IMAGEHLP.

- Les modules qui ont des cadres sur la pile doivent inclure des informations de débogage. S’ils ne contiennent pas d’informations de débogage, la fonction générera toujours une trace de pile, mais la trace sera moins détaillée.

### <a name="requirements"></a>Spécifications

**En-tête:** afx.h

## <a name="afxenablememoryleakdump"></a><a name="afxenablememoryleakdump"></a>AfxEnableMemoryLeakDump AfxEnableMemoryLeakDump

Permet et désactive le dépotoir de fuite de mémoire dans le destructeur AFX_DEBUG_STATE.

```
BOOL AFXAPI AfxEnableMemoryLeakDump(BOOL bDump);
```

### <a name="parameters"></a>Paramètres

*bDump (en)*<br/>
[dans] TRUE indique que le dépotoir de fuite de mémoire est activé; FALSE indique que le dépotoir de fuite de mémoire est désactivé.

### <a name="return-value"></a>Valeur de retour

La valeur précédente pour cet indicateur.

### <a name="remarks"></a>Notes

Quand une application décharge la bibliothèque MFC, cette bibliothèque recherche les fuites de mémoire. À ce stade, toutes les fuites de mémoire sont signalées à l’utilisateur à travers la fenêtre **Debug** de Visual Studio.

Si votre application charge une autre bibliothèque avant la bibliothèque MFC, certaines allocations de mémoire dans cette bibliothèque sont considérées incorrectement comme des fuites de mémoire. Les fausses fuites de mémoire peuvent provoquer la fermeture lente de votre application car la bibliothèque MFC les signale. Dans ce cas, utilisez `AfxEnableMemoryLeakDump` pour désactiver l’image des fuites de mémoire.

> [!NOTE]
> Si vous utilisez cette méthode pour désactiver l’image des fuites de mémoire, vous ne recevez pas d’indication des fuites de mémoire valides dans votre application. Vous devez utiliser cette méthode seulement si vous êtes certain que le rapport sur les fuites de mémoire contient des fausses fuites de mémoire.

### <a name="requirements"></a>Spécifications

**En-tête:** afx.h

## <a name="afxenablememorytracking"></a><a name="afxenablememorytracking"></a>AfxEnableMemoryTracking AfxEnableMemoryTracking AfxEnableMemoryTracking Afx

Le suivi diagnostique de la mémoire est normalement activé dans la version Debug de MFC.

```
BOOL AfxEnableMemoryTracking(BOOL bTrack);
```

### <a name="parameters"></a>Paramètres

*bTrack (en)*<br/>
Définir cette valeur à TRUE active le suivi de la mémoire; FALSE l’éteint.

### <a name="return-value"></a>Valeur de retour

Le réglage précédent du drapeau de suivi-permettant.

### <a name="remarks"></a>Notes

Utilisez cette fonction pour désactiver le suivi sur les sections de votre code que vous savez allouent des blocs correctement.

Pour plus `AfxEnableMemoryTracking`d’informations sur , voir [Debugging MFC Applications](/visualstudio/debugger/mfc-debugging-techniques).

> [!NOTE]
> Cette fonction ne fonctionne que dans la version Debug de MFC.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_Utilities#24](../../mfc/codesnippet/cpp/diagnostic-services_12.cpp)]

### <a name="requirements"></a>Spécifications

**En-tête:** afx.h

## <a name="afxismemoryblock"></a><a name="afxismemoryblock"></a>AfxIsMemoryBlock

Teste une adresse mémoire pour s’assurer qu’elle représente un bloc de mémoire actuellement actif qui a été alloué par la version diagnostique de **nouveau**.

```
BOOL AfxIsMemoryBlock(
    const void* p,
    UINT nBytes,
    LONG* plRequestNumber = NULL);
```

### <a name="parameters"></a>Paramètres

*P*<br/>
Points au bloc de mémoire à tester.

*nBytes (en)*<br/>
Contient la longueur du bloc de mémoire dans les octets.

*plRequestNumber*<br/>
Points à un **long** integer qui sera rempli avec le numéro de séquence d’allocation du bloc de mémoire, ou zéro si elle ne représente pas un bloc de mémoire actuellement actif.

### <a name="return-value"></a>Valeur de retour

Nonzero si le bloc mémoire est actuellement alloué et la longueur est correcte; sinon 0.

### <a name="remarks"></a>Notes

Il vérifie également la taille spécifiée par rapport à la taille d’origine allouée. Si la fonction renvoie nonzero, le numéro de séquence d’allocation est retourné en *plRequestNumber*. Ce numéro représente l’ordre dans lequel le bloc a été attribué par rapport à toutes les autres **nouvelles** allocations.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_Utilities#27](../../mfc/codesnippet/cpp/diagnostic-services_13.cpp)]

### <a name="requirements"></a>Spécifications

**En-tête:** afx.h

## <a name="afxisvalidaddress"></a><a name="afxisvalidaddress"></a>AfxIsValidAddress

Teste n’importe quelle adresse mémoire pour s’assurer qu’elle est entièrement contenue dans l’espace mémoire du programme.

```
BOOL AfxIsValidAddress(
    const void* lp,
    UINT nBytes,
    BOOL bReadWrite = TRUE);
```

### <a name="parameters"></a>Paramètres

*Lp*<br/>
Points à l’adresse mémoire à tester.

*nBytes (en)*<br/>
Contient le nombre d’octets de mémoire à tester.

*bReadWrite (en)*<br/>
Précise si la mémoire est à la fois pour la lecture et l’écriture (TRUE) ou tout simplement la lecture (FALSE).

### <a name="return-value"></a>Valeur de retour

Dans les constructions de débog, nonzero si le bloc de mémoire spécifié est contenu entièrement dans l’espace de mémoire du programme; sinon 0.

Dans les constructions non-debug, nonzero si *lp n’est* pas NULL; sinon 0.

### <a name="remarks"></a>Notes

L’adresse n’est pas limitée aux blocs attribués par **les nouveaux**.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_Utilities#28](../../mfc/codesnippet/cpp/diagnostic-services_14.cpp)]

### <a name="requirements"></a>Spécifications

**En-tête:** afx.h

## <a name="afxisvalidstring"></a><a name="afxisvalidstring"></a>AfxIsValidString AfxIsValidString

Utilisez cette fonction pour déterminer si un pointeur à une chaîne est valide.

```
BOOL  AfxIsValidString(
    LPCSTR lpsz,
    int nLength = -1);
```

### <a name="parameters"></a>Paramètres

*lpsz lpsz*<br/>
Le pointeur à tester.

*nLength (en)*<br/>
Spécifie la longueur de la chaîne à tester, dans les octets. Une valeur de -1 indique que la chaîne sera non terminée.

### <a name="return-value"></a>Valeur de retour

Dans les constructions de débog, nonzero si le pointeur spécifié pointe vers une chaîne de la taille spécifiée; sinon 0.

Dans les constructions non-debug, nonzero si *lpsz n’est* pas NULL; sinon 0.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_Utilities#29](../../mfc/codesnippet/cpp/diagnostic-services_15.cpp)]

### <a name="requirements"></a>Spécifications

**En-tête:** afx.h

## <a name="afxsetallochook"></a><a name="afxsetallochook"></a>AfxSetAllocHook

Définit un crochet qui permet d’appeler la fonction spécifiée avant que chaque bloc de mémoire soit attribué.

```
AFX_ALLOC_HOOK AfxSetAllocHook(AFX_ALLOC_HOOK pfnAllocHook);
```

### <a name="parameters"></a>Paramètres

*pfnAllocHook*<br/>
Spécifie le nom de la fonction à appeler. Voir les remarques pour le prototype d’une fonction d’allocation.

### <a name="return-value"></a>Valeur de retour

Nonzero si vous voulez permettre l’allocation; sinon 0.

### <a name="remarks"></a>Notes

L’alloueur de mémoire de mémoire de classe Microsoft Foundation Class Library peut appeler une fonction de crochet définie par l’utilisateur pour permettre à l’utilisateur de surveiller une allocation de mémoire et de contrôler si l’allocation est autorisée. Les fonctions de crochet d’allocation sont prototypes comme suit :

**BOOL AFXAPI AllocHook ( size_t** `nSize` **, BOOL** `bObject` **, LONG** `lRequestNumber` **);**

*nSize (en)*<br/>
La taille de l’allocation de mémoire proposée.

*bObject*<br/>
VRAI si l’allocation `CObject`est pour un objet dérivé; autrement FALSE.

*lRequestNumber*<br/>
Le numéro de séquence de l’allocation de mémoire.

Notez que la convention d’appel AFXAPI implique que le destinataire doit supprimer les paramètres de la pile.

### <a name="requirements"></a>Spécifications

**En-tête:** afx.h

## <a name="afxdoforallclasses"></a><a name="afxdoforallclasses"></a>AfxDoForAllClasses

Appelle la fonction d’itération spécifiée pour toutes les classes sérialisables `CObject`dérivées dans l’espace mémoire de l’application.

```
void
AFXAPI AfxDoForAllClasses(
    void (* pfn)(const CRuntimeClass* pClass, void* pContext),
    void* pContext);
```

### <a name="parameters"></a>Paramètres

*pfn (pfn)*<br/>
Points à une fonction d’itération à appeler pour chaque classe. Les arguments de fonction `CRuntimeClass` sont un pointeur à un objet et un pointeur vide aux données supplémentaires que l’appelant fournit à la fonction.

*pContext*<br/>
Indique les données facultatives que l’appelant peut fournir à la fonction d’itération. Ce pointeur peut être NULL.

### <a name="remarks"></a>Notes

Les classes `CObject`sérialisables sont des classes dérivées à l’aide de la macro DECLARE_SERIAL. Le pointeur qui `AfxDoForAllClasses` est passé à dans *pContext* est passé à la fonction d’itération spécifiée chaque fois qu’il est appelé.

> [!NOTE]
> Cette fonction ne fonctionne que dans la version Debug de MFC.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#113](../../mfc/codesnippet/cpp/diagnostic-services_16.cpp)]

[!code-cpp[NVC_MFCCollections#114](../../mfc/codesnippet/cpp/diagnostic-services_17.cpp)]

### <a name="requirements"></a>Spécifications

**En-tête:** afx.h

## <a name="afxdoforallobjects"></a><a name="afxdoforallobjects"></a>AfxDoForAllObjects

Exécute la fonction d’itération spécifiée `CObject` pour tous les objets dérivés de ceux qui ont été alloués avec **de nouveaux**.

```
void AfxDoForAllObjects(
    void (* pfn)(CObject* pObject, void* pContext),
    void* pContext);
```

### <a name="parameters"></a>Paramètres

*pfn (pfn)*<br/>
Points à une fonction d’itération à exécuter pour chaque objet. Les arguments de fonction `CObject` sont un pointeur à un pointeur et un pointeur vide aux données supplémentaires que l’appelant fournit à la fonction.

*pContext*<br/>
Indique les données facultatives que l’appelant peut fournir à la fonction d’itération. Ce pointeur peut être NULL.

### <a name="remarks"></a>Notes

Les objets empilés, globaux ou embarqués ne sont pas énumérés. Le pointeur `AfxDoForAllObjects` passé à dans *pContext* est passé à la fonction d’itération spécifiée chaque fois qu’il est appelé.

> [!NOTE]
> Cette fonction ne fonctionne que dans la version Debug de MFC.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#115](../../mfc/codesnippet/cpp/diagnostic-services_18.cpp)]

[!code-cpp[NVC_MFCCollections#116](../../mfc/codesnippet/cpp/diagnostic-services_19.cpp)]

## <a name="see-also"></a>Voir aussi

[Macros et objet Globals](mfc-macros-and-globals.md)<br/>
[CObject::Dump](cobject-class.md#dump)
