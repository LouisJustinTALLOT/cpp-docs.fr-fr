---
title: Macros de débogage et de déclaration d’erreurs
ms.date: 05/06/2019
f1_keywords:
- atldef/ATL::_ATL_DEBUG_INTERFACES
- atldef/ATL::_ATL_DEBUG_QI
- atldef/ATL::ATLASSERT
- afx/ATL::ATLENSURE
- atltrace/ATL::ATLTRACENOTIMPL
- atltrace/ATL::ATLTRACE
helpviewer_keywords:
- macros, error reporting
ms.assetid: 4da9b87f-ec5c-4a32-ab93-637780909b9d
ms.openlocfilehash: 69ab6e17bfb1ec85ddb5b8c19c18010a9b4f3df6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330186"
---
# <a name="debugging-and-error-reporting-macros"></a>Macros de débogage et de déclaration d’erreurs

Ces macros fournissent des installations de débogage et de traces utiles.

|||
|-|-|
|[_ATL_DEBUG_INTERFACES](#_atl_debug_interfaces)|Écrit, à la fenêtre de sortie, toutes `_Module.Term` les fuites d’interface qui sont détectées lorsqu’elles sont appelées.|
|[_ATL_DEBUG_QI](#_atl_debug_qi)|Écrit tous `QueryInterface` les appels à la fenêtre de sortie.|
|[ATLASSERT (EN)](#atlassert)|Effectue la même fonctionnalité que la macro [_ASSERTE](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) trouvée dans la bibliothèque C run-time.|
|[ATLENSURE (ATLENSURE)](#atlensure)|Effectue la validation des paramètres. Appel `AtlThrow` si nécessaire|
|[ATLTRACENOTIMPL](#atltracenotimpl)|Envoie un message à l’appareil de décharge que la fonction spécifiée n’est pas implémentée.|
|[ATLTRACE (EN ANGLAIS)](#atltrace)|Signale les avertissements à un dispositif de sortie, comme la fenêtre de débogé, selon les drapeaux et les niveaux indiqués. Inclus pour la compatibilité vers l’arrière.|
|[ATLTRACE2](#atltrace2)|Signale les avertissements à un dispositif de sortie, comme la fenêtre de débogé, selon les drapeaux et les niveaux indiqués.|

## <a name="_atl_debug_interfaces"></a><a name="_atl_debug_interfaces"></a>_ATL_DEBUG_INTERFACES

Définissez cette macro avant d’inclure `AddRef` tous `Release` les fichiers d’en-tête ATL pour tracer tous et appelle les interfaces de vos composants à la fenêtre de sortie.

```
#define _ATL_DEBUG_INTERFACES
```

### <a name="remarks"></a>Notes

La sortie de trace apparaîtra comme indiqué ci-dessous :

`ATL: QIThunk - 2008         AddRef  :   Object = 0x00d81ba0   Refcount = 1   CBug - IBug`

La première partie de chaque `ATL: QIThunk`trace sera toujours . Ensuite, une valeur identifiant l’interface particulière *thunk* utilisé. Une interface thunk est un objet utilisé pour maintenir un nombre de références et fournir la capacité de traçage utilisée ici. Une nouvelle interface thunk est `QueryInterface` créée sur chaque `IUnknown` appel à l’exception des demandes pour l’interface (dans ce cas, le même thunk est retourné à chaque fois pour se conformer aux règles d’identité de COM).

Ensuite, vous `AddRef` verrez `Release` ou indiquerz quelle méthode a été appelée. Par la suite, vous verrez une valeur identifiant l’objet dont le nombre de références d’interface a été modifié. La valeur tracée est le **pointeur** de l’objet.

Le nombre de références qui est tracé est le `AddRef` `Release` compte de référence sur ce thunk après ou a été appelé. Notez que ce nombre de références peut ne pas correspondre au nombre de références pour l’objet. Chaque thunk maintient son propre nombre de références pour vous aider à vous conformer pleinement aux règles de comptage des références de COM.

La dernière information retrouvée est le nom de l’objet `AddRef` et `Release` l’interface affectée par l’ou l’appel.

Toutes les fuites d’interface qui sont `_Module.Term` détectées lorsque le serveur s’arrête et est appelé seront enregistrés comme ceci:

`ATL: QIThunk - 2005         LEAK    :   Object = 0x00d81ca0   Refcount = 1   MaxRefCount = 1   CBug - IBug`

Les informations fournies ici sont directement les informations fournies dans les relevés de traces précédents, afin que vous puissiez examiner les comptes de référence tout au long de la durée de vie d’une interface thunk. En outre, vous obtenez une indication du nombre maximum de référence sur cette interface thunk.

> [!NOTE]
> _ATL_DEBUG_INTERFACES peuvent être utilisés dans les constructions de détail.

## <a name="_atl_debug_qi"></a><a name="_atl_debug_qi"></a>_ATL_DEBUG_QI

Écrit tous `QueryInterface` les appels à la fenêtre de sortie.

```
#define _ATL_DEBUG_QI
```

### <a name="remarks"></a>Notes

Si un `QueryInterface` appel a échoué, la fenêtre de sortie s’affichera :

*nom de l’interface* - `failed`

## <a name="atlassert"></a><a name="atlassert"></a>ATLASSERT (EN)

La macro ATLASSERT effectue la même fonctionnalité que la macro [_ASSERTE](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) que l’on trouve dans la bibliothèque C run-time.

```
ATLASSERT(booleanExpression);
```

### <a name="parameters"></a>Paramètres

*booleanExpression*<br/>
Expression (pointeurs inclus) qui prend une valeur différente de zéro ou 0.

### <a name="remarks"></a>Notes

Dans les constructions de débog, ATLASSERT évalue *booleanExpression* et génère un rapport de débbug lorsque le résultat est faux.

## <a name="requirements"></a>Spécifications

**En-tête:** atldef.h

## <a name="atlensure"></a><a name="atlensure"></a>ATLENSURE (ATLENSURE)

Cette macro est utilisée pour valider les paramètres transmis à une fonction.

```
ATLENSURE(booleanExpression);
ATLENSURE_THROW(booleanExpression, hr);
```

### <a name="parameters"></a>Paramètres

*booleanExpression*<br/>
Spécifie une expression boolean à tester.

*Hr*<br/>
Spécifie un code d’erreur à retourner.

### <a name="remarks"></a>Notes

Ces macros fournissent un mécanisme pour détecter et informer l’utilisateur de l’utilisation incorrecte des paramètres.

La macro appelle ATLASSERT et `AtlThrow`si la condition échoue appels .

Dans le cas ATLENSURE, `AtlThrow` est appelé avec E_FAIL.

Dans le cas ATLENSURE_THROW, `AtlThrow` est appelé avec le HRESULT spécifié.

La différence entre ATLENSURE et ATLASSERT est qu’ATLENSURE jette une exception dans Release construit ainsi que dans Debug construit.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#108](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_1.cpp)]

## <a name="requirements"></a>Spécifications

**En-tête:** afx.h

## <a name="atltracenotimpl"></a><a name="atltracenotimpl"></a>ATLTRACENOTIMPL

Dans les constructions de débog d’ATL, envoie la chaîne *"funcname n’est* pas implémenté" à l’appareil de décharge et retourne E_NOTIMPL.

```
ATLTRACENOTIMPL(funcname);
```

### <a name="parameters"></a>Paramètres

*Funcname*<br/>
[dans] Une chaîne contenant le nom de la fonction qui n’est pas implémentée.

### <a name="remarks"></a>Notes

Dans les versions, il suffit de retourner E_NOTIMPL.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#127](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_2.cpp)]

## <a name="requirements"></a>Spécifications

**En-tête:** atltrace.h

## <a name="atltrace"></a><a name="atltrace"></a>ATLTRACE (EN ANGLAIS)

Signale les avertissements à un dispositif de sortie, comme la fenêtre de débogé, selon les drapeaux et les niveaux indiqués. Inclus pour la compatibilité vers l’arrière.

```
ATLTRACE(exp);

ATLTRACE(
    DWORD category,
    UINT  level,
    LPCSTR lpszFormat, ...);
```

### <a name="parameters"></a>Paramètres

*Exp*<br/>
[dans] La chaîne et les variables à envoyer à la fenêtre de sortie ou toute application qui piège ces messages.

*Catégorie*<br/>
[dans] Type d’événement ou méthode sur lequel signaler. Voir les remarques pour une liste de catégories.

*Niveau*<br/>
[dans] Le niveau de traçage à signaler. Voir les remarques pour plus de détails.

*lpszFormat (en)*<br/>
[dans] La chaîne formatée à envoyer à l’appareil de décharge.

### <a name="remarks"></a>Notes

Voir [ATLTRACE2](#atltrace2) pour une description de ATLTRACE. ATLTRACE et ATLTRACE2 ont le même comportement, ATLTRACE est inclus pour la compatibilité vers l’arrière.

## <a name="atltrace2"></a><a name="atltrace2"></a>ATLTRACE2

Signale les avertissements à un dispositif de sortie, comme la fenêtre de débogé, selon les drapeaux et les niveaux indiqués.

```
ATLTRACE2(exp);

ATLTRACE2(
    DWORD category,
    UINT level,
    LPCSTR lpszFormat,  ...);
```

### <a name="parameters"></a>Paramètres

*Exp*<br/>
[dans] La chaîne à envoyer à la fenêtre de sortie ou toute application qui piège ces messages.

*Catégorie*<br/>
[dans] Type d’événement ou méthode sur lequel signaler. Voir les remarques pour une liste de catégories.

*Niveau*<br/>
[dans] Le niveau de traçage à signaler. Voir les remarques pour plus de détails.

*lpszFormat (en)*<br/>
[dans] La `printf`chaîne de format de style à utiliser pour créer une chaîne à envoyer à l’appareil de décharge.

### <a name="remarks"></a>Notes

La forme courte d’ATLTRACE2 écrit une chaîne à la fenêtre de sortie du débagé. La deuxième forme d’ATLTRACE2 est également la sortie de la fenêtre de sortie du débagé, mais est soumise aux paramètres de l’outil de trace ATL/MFC (voir [ATLTraceTool Sample](../../overview/visual-cpp-samples.md)). Par exemple, si vous définissez le *niveau* à 4 et l’outil de trace ATL/MFC au niveau 0, vous ne verrez pas le message. *niveau* peut être de 0, 1, 2, 3 ou 4. La valeur par défaut, 0, ne signale que les problèmes les plus graves.

Le paramètre *de catégorie* répertorie les traces à définir. Ces drapeaux correspondent aux types de méthodes pour lesquelles vous souhaitez signaler. Les tableaux ci-dessous dressent la liste des traces valides que vous pouvez utiliser pour le paramètre de la *catégorie.*

### <a name="atl-trace-flags"></a>ATL Trace Flags

|Catégorie ATL|Description|
|------------------|-----------------|
|`atlTraceGeneral`|Rapports sur toutes les applications ATL. Valeur par défaut.|
|`atlTraceCOM`|Rapports sur les méthodes COM.|
|`atlTraceQI`|Rapports sur les appels De RequêteInterface.|
|`atlTraceRegistrar`|Rapports sur l’enregistrement des objets.|
|`atlTraceRefcount`|Rapports sur l’évolution du nombre de références.|
|`atlTraceWindowing`|Rapports sur les méthodes windows; par exemple, signale une carte de message invalide ID.|
|`atlTraceControls`|Rapports sur les contrôles; par exemple, les rapports lorsqu’un contrôle ou sa fenêtre est détruit.|
|`atlTraceHosting`|Rapports hébergeant des messages; par exemple, les rapports lorsqu’un client dans un conteneur est activé.|
|`atlTraceDBClient`|Rapports sur OLE DB Consumer Template; par exemple, lorsqu’un appel à GetData échoue, la sortie peut contenir le HRESULT.|
|`atlTraceDBProvider`|Rapports sur OLE DB Provider Template; par exemple, signale si la création d’une colonne a échoué.|
|`atlTraceSnapin`|Rapports pour l’application SnapIn MMC.|
|`atlTraceNotImpl`|Rapports que la fonction indiquée n’est pas mis en œuvre.|
|`atlTraceAllocation`|Rapports messages imprimés par les outils de débogage de mémoire dans atldbgmem.h.|

### <a name="mfc-trace-flags"></a>Drapeaux trace MFC

|Catégorie MFC|Description|
|------------------|-----------------|
|`traceAppMsg`|But général, messages MFC. Toujours recommandé.|
|`traceDumpContext`|Messages de [CDumpContext](../../mfc/reference/cdumpcontext-class.md).|
|`traceWinMsg`|Messages du code de traitement des messages de MFC.|
|`traceMemory`|Messages du code de gestion de la mémoire de MFC.|
|`traceCmdRouting`|Messages du code de routage windows de MFC.|
|`traceHtml`|Messages de MFC DHTML dialogue support.|
|`traceSocket`|Messages de la prise de MFC support.|
|`traceOle`|Messages du support OLE de MFC.|
|`traceDatabase`|Messages de la base de données de MFC support.|
|`traceInternet`|Messages du support Internet de MFC.|

Pour déclarer une catégorie de traces `CTraceCategory` personnalisées, déclarez une instance globale de la classe comme suit :

[!code-cpp[NVC_ATL_Utilities#109](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_3.cpp)]

Le nom de la catégorie, MY_CATEGORY dans cet exemple, est le nom que vous spécifiez au paramètre *de* catégorie. Le premier paramètre est le nom de catégorie qui apparaîtra dans l’outil de trace ATL/MFC. Le deuxième paramètre est le niveau de trace par défaut. Ce paramètre est facultatif, et le niveau de trace par défaut est de 0.

Pour utiliser une catégorie définie par l’utilisateur :

[!code-cpp[NVC_ATL_Utilities#110](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_4.cpp)]

Pour spécifier que vous souhaitez filtrer les messages de trace, insérez des définitions pour ces macros dans Stdafx.h avant la `#include <atlbase.h>` déclaration.

Alternativement, vous pouvez définir le filtre dans les directives de préprocesseur dans la boîte de dialogue **des pages de propriété.** Cliquez sur l’onglet **Preprocessor,** puis insérez le global dans la boîte **d’édition de définitions de préprocesseur.**

Atlbase.h contient des définitions par défaut des macros ATLTRACE2 et ces définitions seront utilisées si vous ne définissez pas ces symboles avant que atlbase.h ne soit traité.

Dans les versions, ATLTRACE2 `(void) 0`compile à .

ATLTRACE2 limite le contenu de la chaîne à envoyer à l’appareil de décharge à pas plus de 1023 caractères, après le formatage.

ATLTRACE et ATLTRACE2 ont le même comportement, ATLTRACE est inclus pour la compatibilité vers l’arrière.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#111](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_5.cpp)]

## <a name="see-also"></a>Voir aussi

[Macros](../../atl/reference/atl-macros.md)<br/>
[Débogage et déclaration d’erreurs Fonctions mondiales](../../atl/reference/debugging-and-error-reporting-global-functions.md)
