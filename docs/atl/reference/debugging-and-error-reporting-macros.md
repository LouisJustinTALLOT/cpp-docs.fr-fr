---
title: Macros de débogage et rapport d’erreurs
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
ms.openlocfilehash: a243351ff337cb517f8a8231c18c495c8d2ca302
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65221075"
---
# <a name="debugging-and-error-reporting-macros"></a>Macros de débogage et rapport d’erreurs

Ces macros fournissent des fonctionnalités de trace et de débogage utiles.

|||
|-|-|
|[_ATL_DEBUG_INTERFACES](#_atl_debug_interfaces)|Écrit dans la fenêtre Sortie, les fuites de n’importe quelle interface qui sont détectés lorsque `_Module.Term` est appelée.|
|[_ATL_DEBUG_QI](#_atl_debug_qi)|Écrit tous les appels à `QueryInterface` dans la fenêtre Sortie.|
|[ATLASSERT](#atlassert)|Effectue les mêmes fonctionnalités que le [_ASSERTE](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) macro trouvé dans la bibliothèque Runtime C.|
|[ATLENSURE](#atlensure)|Effectue une validation de paramètres. Appeler `AtlThrow` si nécessaire|
|[ATLTRACENOTIMPL](#atltracenotimpl)|Envoie un message à l’unité de sauvegarde que la fonction spécifiée n’est pas implémentée.|
|[ATLTRACE](#atltrace)|Signale les avertissements pour un périphérique de sortie, tels que la fenêtre du débogueur, selon les indicateurs indiqués et les niveaux. Inclus pour la compatibilité descendante.|
|[ATLTRACE2](#atltrace2)|Signale les avertissements pour un périphérique de sortie, tels que la fenêtre du débogueur, selon les indicateurs indiqués et les niveaux.|

##  <a name="_atl_debug_interfaces"></a>  _ATL_DEBUG_INTERFACES

Définir cette macro avant d’inclure les fichiers d’en-tête ATL pour suivre toutes les `AddRef` et `Release` appelle sur les interfaces de vos composants dans la fenêtre Sortie.

```
#define _ATL_DEBUG_INTERFACES
```

### <a name="remarks"></a>Notes

La sortie de trace s’affiche comme indiqué ci-dessous :

`ATL: QIThunk - 2008         AddRef  :   Object = 0x00d81ba0   Refcount = 1   CBug - IBug`

La première partie de chaque trace sera toujours `ATL: QIThunk`. Est ensuite une valeur qui identifie le particulier *interface thunk* utilisé. Un thunk de l’interface est un objet utilisé pour maintenir un décompte de références et de fournir la fonctionnalité de suivi utilisée ici. Un thunk interface nouveau est créé à chaque appel à `QueryInterface` à l’exception des demandes pour le `IUnknown` interface (dans ce cas, le thunk même revient systématiquement pour se conformer aux règles d’identité de COM).

Ensuite, vous verrez `AddRef` ou `Release` indiquant quelle méthode a été appelée. Ensuite, vous verrez une valeur qui identifie l’objet dont le nombre de référence interface a été modifié. La valeur de suivi est le **cela** pointeur de l’objet.

Le décompte de références faisant l’objet est le nombre de références sur ce thunk après `AddRef` ou `Release` a été appelée. Notez que ce nombre de référence peut ne pas correspond le décompte de références pour l’objet. Chaque thunk conserve son propre comptage des références pour vous aider à entièrement conforme aux règles de comptage de références de COM.

La dernière pièce du suivi d’informations est le nom de l’objet et l’interface soient affectés par la `AddRef` ou `Release` appeler.

N’importe quelle interface fuites détectées lorsque le serveur s’arrête et `_Module.Term` est appelé s’être connecté comme suit :

`ATL: QIThunk - 2005         LEAK    :   Object = 0x00d81ca0   Refcount = 1   MaxRefCount = 1   CBug - IBug`

Les informations fournies ici est directement mappée aux informations fournies dans les instructions de trace précédente, afin de pouvoir examiner les décomptes de références tout au long de la durée de vie entier d’une conversion de code d’interface. En outre, vous obtenez une indication du nombre maximal de références sur ce thunk de l’interface.

> [!NOTE]
> _ATL_DEBUG_INTERFACES peut être utilisé dans les versions commerciales.

##  <a name="_atl_debug_qi"></a>  _ATL_DEBUG_QI

Écrit tous les appels à `QueryInterface` dans la fenêtre Sortie.

```
#define _ATL_DEBUG_QI
```

### <a name="remarks"></a>Notes

Si un appel à `QueryInterface` a échoué, la fenêtre Sortie affiche :

*nom de l’interface* - `failed`

##  <a name="atlassert"></a>  ATLASSERT

La macro ATLASSERT ; effectue les mêmes fonctionnalités que le [_ASSERTE](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) macro trouvé dans la bibliothèque Runtime C.

```
ATLASSERT(booleanExpression);
```

### <a name="parameters"></a>Paramètres

*booleanExpression*<br/>
Expression (pointeurs inclus) qui prend une valeur différente de zéro ou 0.

### <a name="remarks"></a>Notes

Dans les versions debug, évalue ATLASSERT ; *booleanExpression* et génère un rapport de débogage lorsque le résultat est false.

## <a name="requirements"></a>Configuration requise

**En-tête :** atldef.h

##  <a name="atlensure"></a>  ATLENSURE

Cette macro est utilisée pour valider les paramètres passés à une fonction.

```
ATLENSURE(booleanExpression);
ATLENSURE_THROW(booleanExpression, hr);
```

### <a name="parameters"></a>Paramètres

*booleanExpression*<br/>
Spécifie une expression booléenne à tester.

*hr*<br/>
Spécifie un code d’erreur à retourner.

### <a name="remarks"></a>Notes

Ces macros fournissent un mécanisme permettant de détecter et en informer l’utilisateur de l’utilisation des paramètres incorrects.

La macro appelle ATLASSERT ; et si la condition échoue appelle `AtlThrow`.

Dans le cas ATLENSURE, `AtlThrow` est appelée avec E_FAIL.

Dans le cas ATLENSURE_THROW, `AtlThrow` est appelée avec la valeur HRESULT spécifiée.

La différence entre ATLENSURE et ATLASSERT ; est que ATLENSURE lève une exception dans les versions Release, ainsi que dans les versions Debug.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#108](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_1.cpp)]

## <a name="requirements"></a>Configuration requise

**En-tête :** afx.h

##  <a name="atltracenotimpl"></a>  ATLTRACENOTIMPL

Dans les versions debug d’ATL, envoie la chaîne « *funcname* n’est pas implémentée » à l’unité de sauvegarde et la retourne E_NOTIMPL.

```
ATLTRACENOTIMPL(funcname);
```

### <a name="parameters"></a>Paramètres

*funcname*<br/>
[in] Chaîne contenant le nom de la fonction qui n’est pas implémentée.

### <a name="remarks"></a>Notes

Dans les versions release, renvoie simplement E_NOTIMPL.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#127](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_2.cpp)]

## <a name="requirements"></a>Configuration requise

**En-tête :** atltrace.h

##  <a name="atltrace"></a>  ATLTRACE

Signale les avertissements pour un périphérique de sortie, tels que la fenêtre du débogueur, selon les indicateurs indiqués et les niveaux. Inclus pour la compatibilité descendante.

```
ATLTRACE(exp);

ATLTRACE(
    DWORD category,
    UINT  level,
    LPCSTR lpszFormat, ...);
```

### <a name="parameters"></a>Paramètres

*exp*<br/>
[in] La chaîne et les variables à envoyer à la fenêtre Sortie ou de n’importe quelle application qui intercepte ces messages.

*category*<br/>
[in] Type d’événement ou méthode sur lequel au rapport. Consultez la section Notes pour obtenir la liste des catégories.

*level*<br/>
[in] Le niveau de suivi pour le rapport. Consultez la section Notes pour plus d’informations.

*lpszFormat*<br/>
[in] La chaîne mise en forme pour envoyer à l’unité de vidage.

### <a name="remarks"></a>Notes

Consultez [ATLTRACE2](#atltrace2) pour obtenir une description de ATLTRACE. ATLTRACE et ATLTRACE2 ont le même comportement, ATLTRACE est inclus pour la compatibilité descendante.

##  <a name="atltrace2"></a>  ATLTRACE2

Signale les avertissements pour un périphérique de sortie, tels que la fenêtre du débogueur, selon les indicateurs indiqués et les niveaux.

```
ATLTRACE2(exp);

ATLTRACE2(
    DWORD category,
    UINT level,
    LPCSTRlpszFormat,  ...);
```

### <a name="parameters"></a>Paramètres

*exp*<br/>
[in] Chaîne à envoyer à la fenêtre Sortie ou de n’importe quelle application qui intercepte ces messages.

*category*<br/>
[in] Type d’événement ou méthode sur lequel au rapport. Consultez la section Notes pour obtenir la liste des catégories.

*level*<br/>
[in] Le niveau de suivi pour le rapport. Consultez la section Notes pour plus d’informations.

*lpszFormat*<br/>
[in] Le `printf`-style de chaîne de format à utiliser pour créer une chaîne à envoyer à l’unité de vidage.

### <a name="remarks"></a>Notes

La forme abrégée de ATLTRACE2 écrit une chaîne dans la fenêtre du débogueur sortie. La deuxième forme de ATLTRACE2 également écrit la sortie dans la fenêtre de sortie du débogueur, mais est fonction des paramètres de l’ATL/MFC Trace Tool (consultez [exemple ATLTraceTool](../../overview/visual-cpp-samples.md)). Par exemple, si vous définissez *niveau* de 4 et de l’ATL/MFC Trace Tool au niveau 0, vous ne verrez pas le message. *niveau* peut être 0, 1, 2, 3 ou 4. Les rapports par défaut, 0, seuls les problèmes plus graves.

Le *catégorie* paramètre répertorie les indicateurs de trace à définir. Ces indicateurs correspondent aux types des méthodes pour lequel vous souhaitez signaler. Les tableaux ci-dessous répertorient les indicateurs de trace valide que vous pouvez utiliser pour le *catégorie* paramètre.

### <a name="atl-trace-flags"></a>Indicateurs de Trace ATL

|Catégorie d’ATL|Description|
|------------------|-----------------|
|`atlTraceGeneral`|Rapports sur toutes les applications ATL. Valeur par défaut.|
|`atlTraceCOM`|Rapports sur les méthodes COM.|
|`atlTraceQI`|Rapports sur les appels QueryInterface.|
|`atlTraceRegistrar`|Rapports sur l’inscription d’objets.|
|`atlTraceRefcount`|Rapports sur la modification de décompte de références.|
|`atlTraceWindowing`|Rapports sur les méthodes de windows ; par exemple, signale un ID de mappage de message non valide.|
|`atlTraceControls`|Rapports sur les contrôles ; par exemple, rapports lorsqu’un contrôle ou sa fenêtre est détruite.|
|`atlTraceHosting`|Rapports qui héberge les messages ; par exemple, signale quand un client dans un conteneur est activé.|
|`atlTraceDBClient`|Rapports sur le modèle de consommateur OLE DB ; par exemple, lorsqu’un appel à GetData échoue, la sortie peut contenir la valeur HRESULT.|
|`atlTraceDBProvider`|Rapports sur le modèle de fournisseur OLE DB ; par exemple, indique si la création d’une colonne a échoué.|
|`atlTraceSnapin`|Rapports pour l’application du composant logiciel enfichable MMC.|
|`atlTraceNotImpl`|Signale que la fonction indiquée n’est pas implémentée.|
|`atlTraceAllocation`|Rapports des messages par l’outils de débogage dans atldbgmem.h de mémoire.|

### <a name="mfc-trace-flags"></a>Indicateurs de Trace MFC

|Catégorie MFC|Description|
|------------------|-----------------|
|`traceAppMsg`|Usage général, les messages MFC. Toujours recommandée.|
|`traceDumpContext`|Les messages provenant de [CDumpContext](../../mfc/reference/cdumpcontext-class.md).|
|`traceWinMsg`|Messages à partir de code de gestion de messages de MFC.|
|`traceMemory`|Messages à partir du code de gestion de mémoire de MFC.|
|`traceCmdRouting`|Code de routage de commande de messages à partir Windows de MFC.|
|`traceHtml`|Messages à partir de la prise en charge de la boîte de dialogue MFC DHTML.|
|`traceSocket`|Messages à partir de la prise en charge du socket de MFC.|
|`traceOle`|Messages à partir de la prise en charge MFC OLE.|
|`traceDatabase`|Messages à partir de la prise en charge de la base de données de MFC.|
|`traceInternet`|Messages à partir d’Internet MFC prennent en charge.|

Pour déclarer une catégorie de suivi personnalisé, déclarer une instance globale de la `CTraceCategory` classe comme suit :

[!code-cpp[NVC_ATL_Utilities#109](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_3.cpp)]

Le nom de catégorie, MY_CATEGORY dans cet exemple, est le nom que vous spécifiez pour le *catégorie* paramètre. Le premier paramètre est le nom de catégorie qui apparaîtra dans les ATL/MFC Trace Tool. Le deuxième paramètre est le niveau de trace par défaut. Ce paramètre est facultatif et le niveau de trace par défaut est 0.

Pour utiliser une catégorie définie par l’utilisateur :

[!code-cpp[NVC_ATL_Utilities#110](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_4.cpp)]

Pour spécifier que vous souhaitez filtrer les messages de trace, insérez les définitions de ces macros dans Stdafx.h avant la `#include <atlbase.h>` instruction.

Vous pouvez également définir le filtre dans les directives de préprocesseur dans le **Pages de propriétés** boîte de dialogue. Cliquez sur le **préprocesseur** onglet, puis insérez global dans le **définitions de préprocesseur** zone d’édition.

Atlbase.h contient des définitions par défaut des macros ATLTRACE2 et ces définitions sont utilisées si vous ne définissez pas ces symboles avant le traitement d’atlbase.h.

Dans les versions release, ATLTRACE2 se compile en `(void) 0`.

ATLTRACE2 limite le contenu de la chaîne à être envoyés à l’appareil de vidage pour pas plus de 1023 caractères, après la mise en forme.

ATLTRACE et ATLTRACE2 ont le même comportement, ATLTRACE est inclus pour la compatibilité descendante.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#111](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_5.cpp)]

## <a name="see-also"></a>Voir aussi

[Macros](../../atl/reference/atl-macros.md)<br/>
[Fonctions globales de signalement d’erreurs et de débogage](../../atl/reference/debugging-and-error-reporting-global-functions.md)
