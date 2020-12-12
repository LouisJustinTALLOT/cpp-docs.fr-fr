---
description: En savoir plus sur les macros de débogage et de création de rapports d’erreurs
title: Macros de débogage et de rapport d’erreurs
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
ms.openlocfilehash: 573c3f341ff9f9df58337b75e1080dde960d232c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97139943"
---
# <a name="debugging-and-error-reporting-macros"></a>Macros de débogage et de rapport d’erreurs

Ces macros fournissent des fonctionnalités de débogage et de suivi utiles.

|Nom|Description|
|-|-|
|[_ATL_DEBUG_INTERFACES](#_atl_debug_interfaces)|Écrit, dans la fenêtre sortie, les fuites d’interface détectées quand `_Module.Term` est appelé.|
|[_ATL_DEBUG_QI](#_atl_debug_qi)|Écrit tous les appels à dans `QueryInterface` la fenêtre sortie.|
|[ATLASSERT](#atlassert)|Exécute les mêmes fonctionnalités que la macro [_ASSERTE](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) trouvée dans la bibliothèque Runtime C.|
|[ATLENSURE](#atlensure)|Effectue la validation des paramètres. Appeler `AtlThrow` si nécessaire|
|[ATLTRACENOTIMPL](#atltracenotimpl)|Envoie un message à l’appareil de vidage indiquant que la fonction spécifiée n’est pas implémentée.|
|[ATLTRACE](#atltrace)|Signale les avertissements à un périphérique de sortie, tel que la fenêtre du débogueur, en fonction des indicateurs et des niveaux indiqués. Inclus pour la compatibilité descendante.|
|[ATLTRACE2](#atltrace2)|Signale les avertissements à un périphérique de sortie, tel que la fenêtre du débogueur, en fonction des indicateurs et des niveaux indiqués.|

## <a name="_atl_debug_interfaces"></a><a name="_atl_debug_interfaces"></a> _ATL_DEBUG_INTERFACES

Définissez cette macro avant d’inclure des fichiers d’en-tête ATL pour suivre tous les `AddRef` `Release` appels et sur les interfaces de vos composants dans la fenêtre sortie.

```
#define _ATL_DEBUG_INTERFACES
```

### <a name="remarks"></a>Notes

La sortie du suivi s’affiche comme indiqué ci-dessous :

`ATL: QIThunk - 2008         AddRef  :   Object = 0x00d81ba0   Refcount = 1   CBug - IBug`

La première partie de chaque trace sera toujours `ATL: QIThunk` . Next est une valeur identifiant le *thunk d’interface* particulier utilisé. Un thunk d’interface est un objet utilisé pour conserver un décompte de références et fournir la fonctionnalité de traçage utilisée ici. Un nouveau thunk d’interface est créé à chaque appel à `QueryInterface` Except pour les demandes d' `IUnknown` interface (dans ce cas, le même thunk est retourné chaque fois pour se conformer aux règles d’identité de com).

Ensuite, vous verrez `AddRef` ou `Release` Indiquez quelle méthode a été appelée. Après cela, vous verrez une valeur identifiant l’objet dont le décompte de références d’interface a été modifié. La valeur traced est le **`this`** pointeur de l’objet.

Le nombre de références suivi est le nombre de références sur ce thunk après l' `AddRef` appel de ou de `Release` . Notez que ce nombre de références peut ne pas correspondre au nombre de références pour l’objet. Chaque thunk gère son propre nombre de références pour vous aider à se conformer pleinement aux règles de décompte de références de COM.

La dernière information tracée est le nom de l’objet et l’interface affectée par l' `AddRef` appel de ou `Release` .

Les fuites d’interface détectées lorsque le serveur s’arrête et `_Module.Term` sont appelées sont enregistrées de la manière suivante :

`ATL: QIThunk - 2005         LEAK    :   Object = 0x00d81ca0   Refcount = 1   MaxRefCount = 1   CBug - IBug`

Les informations fournies ici correspondent directement aux informations fournies dans les instructions de suivi précédentes, ce qui vous permet d’examiner les décomptes de références pendant toute la durée de vie d’un thunk d’interface. En outre, vous pouvez avoir une indication du nombre maximal de références sur ce thunk d’interface.

> [!NOTE]
> Les _ATL_DEBUG_INTERFACES peuvent être utilisés dans les versions commerciales.

## <a name="_atl_debug_qi"></a><a name="_atl_debug_qi"></a> _ATL_DEBUG_QI

Écrit tous les appels à dans `QueryInterface` la fenêtre sortie.

```
#define _ATL_DEBUG_QI
```

### <a name="remarks"></a>Notes

En cas d’échec d’un appel à `QueryInterface` , la fenêtre sortie affiche :

*nom de l’interface* - `failed`

## <a name="atlassert"></a><a name="atlassert"></a> ATLASSERT

La macro ATLASSERT effectue les mêmes fonctionnalités que la macro [_ASSERTE](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) trouvée dans la bibliothèque Runtime C.

```
ATLASSERT(booleanExpression);
```

### <a name="parameters"></a>Paramètres

*booleanExpression*<br/>
Expression (pointeurs inclus) qui prend une valeur différente de zéro ou 0.

### <a name="remarks"></a>Notes

Dans les versions Debug, ATLASSERT évalue *booleanExpression* et génère un rapport de débogage lorsque le résultat est false.

### <a name="requirements"></a>Spécifications

**En-tête :** atldef. h

## <a name="atlensure"></a><a name="atlensure"></a> ATLENSURE

Cette macro est utilisée pour valider les paramètres passés à une fonction.

```
ATLENSURE(booleanExpression);
ATLENSURE_THROW(booleanExpression, hr);
```

### <a name="parameters"></a>Paramètres

*booleanExpression*<br/>
Spécifie une expression booléenne à tester.

*heure(s)*<br/>
Spécifie un code d’erreur à retourner.

### <a name="remarks"></a>Notes

Ces macros fournissent un mécanisme permettant de détecter et d’informer l’utilisateur d’une utilisation incorrecte des paramètres.

La macro appelle ATLASSERT et si la condition échoue aux appels `AtlThrow` .

Dans le cas ATLENSURE, `AtlThrow` est appelé avec E_FAIL.

Dans le cas ATLENSURE_THROW, `AtlThrow` est appelé avec le HRESULT spécifié.

La différence entre ATLENSURE et ATLASSERT est que ATLENSURE lève une exception dans les versions release et dans les versions Debug.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#108](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_1.cpp)]

### <a name="requirements"></a>Spécifications

**En-tête :** AFX. h

## <a name="atltracenotimpl"></a><a name="atltracenotimpl"></a> ATLTRACENOTIMPL

Dans les versions Debug d’ATL, envoie la chaîne « *funcname* n’est pas implémentée » au périphérique de vidage et retourne E_NOTIMPL.

```
ATLTRACENOTIMPL(funcname);
```

### <a name="parameters"></a>Paramètres

*funcname*<br/>
dans Chaîne contenant le nom de la fonction qui n’est pas implémentée.

### <a name="remarks"></a>Notes

Dans les versions release, retourne simplement E_NOTIMPL.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#127](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_2.cpp)]

### <a name="requirements"></a>Spécifications

**En-tête :** ATLTRACE. h

## <a name="atltrace"></a><a name="atltrace"></a> ATLTRACE

Signale les avertissements à un périphérique de sortie, tel que la fenêtre du débogueur, en fonction des indicateurs et des niveaux indiqués. Inclus pour la compatibilité descendante.

```
ATLTRACE(exp);

ATLTRACE(
    DWORD category,
    UINT  level,
    LPCSTR lpszFormat, ...);
```

### <a name="parameters"></a>Paramètres

*exp*<br/>
dans Chaîne et variables à envoyer à la fenêtre sortie ou à toute application qui intercepte ces messages.

*category*<br/>
dans Type d’événement ou de méthode à signaler. Consultez les notes pour obtenir la liste des catégories.

*level*<br/>
dans Niveau de suivi à signaler. Pour plus d’informations, consultez les notes.

*lpszFormat*<br/>
dans Chaîne mise en forme à envoyer au périphérique de vidage.

### <a name="remarks"></a>Notes

Consultez [ATLTRACE2](#atltrace2) pour obtenir une description de ATLTRACE. ATLTRACE et ATLTRACE2 ont le même comportement, ATLTRACE est inclus à des fins de compatibilité descendante.

## <a name="atltrace2"></a><a name="atltrace2"></a> ATLTRACE2

Signale les avertissements à un périphérique de sortie, tel que la fenêtre du débogueur, en fonction des indicateurs et des niveaux indiqués.

```
ATLTRACE2(exp);

ATLTRACE2(
    DWORD category,
    UINT level,
    LPCSTR lpszFormat,  ...);
```

### <a name="parameters"></a>Paramètres

*exp*<br/>
dans Chaîne à envoyer à la fenêtre sortie ou à n’importe quelle application qui intercepte ces messages.

*category*<br/>
dans Type d’événement ou de méthode à signaler. Consultez les notes pour obtenir la liste des catégories.

*level*<br/>
dans Niveau de suivi à signaler. Pour plus d’informations, consultez les notes.

*lpszFormat*<br/>
dans `printf`Chaîne de format de style à utiliser pour créer une chaîne à envoyer au périphérique de vidage.

### <a name="remarks"></a>Notes

La forme abrégée de ATLTRACE2 écrit une chaîne dans la fenêtre de sortie du débogueur. La deuxième forme de ATLTRACE2 écrit également la sortie dans la fenêtre de sortie du débogueur, mais elle est soumise aux paramètres de l’outil de trace ATL/MFC (consultez [exemple ATLTraceTool](../../overview/visual-cpp-samples.md)). Par exemple, si vous définissez *niveau* sur 4 et l’outil de trace ATL/MFC sur le niveau 0, le message ne s’affiche pas. le *niveau* peut être 0, 1, 2, 3 ou 4. La valeur par défaut, 0, signale uniquement les problèmes les plus graves.

Le paramètre *Category* répertorie les indicateurs de trace à définir. Ces indicateurs correspondent aux types de méthodes pour lesquels vous souhaitez effectuer un rapport. Les tableaux ci-dessous répertorient les indicateurs de trace valides que vous pouvez utiliser pour le paramètre *Category* .

### <a name="atl-trace-flags"></a>Indicateurs de trace ATL

|Catégorie ATL|Description|
|------------------|-----------------|
|`atlTraceGeneral`|Génère des rapports sur toutes les applications ATL. Valeur par défaut.|
|`atlTraceCOM`|Génère des rapports sur les méthodes COM.|
|`atlTraceQI`|Signale les appels QueryInterface.|
|`atlTraceRegistrar`|Signale l’inscription des objets.|
|`atlTraceRefcount`|Signale la modification du nombre de références.|
|`atlTraceWindowing`|Rapports sur les méthodes Windows ; par exemple, signale un ID de table des messages non valide.|
|`atlTraceControls`|Rapports sur les contrôles ; par exemple, signale le moment où un contrôle ou sa fenêtre sont détruits.|
|`atlTraceHosting`|Rapports hébergeant des messages ; par exemple, signale qu’un client d’un conteneur est activé.|
|`atlTraceDBClient`|Rapports sur OLE DB modèle de consommateur ; par exemple, lorsqu’un appel à GetData échoue, la sortie peut contenir le HRESULT.|
|`atlTraceDBProvider`|Rapports sur OLE DB modèle de fournisseur ; par exemple, indique si la création d’une colonne a échoué.|
|`atlTraceSnapin`|Rapports pour l’application de composant logiciel enfichable MMC.|
|`atlTraceNotImpl`|Signale que la fonction indiquée n’est pas implémentée.|
|`atlTraceAllocation`|Signale les messages imprimés par les outils de débogage de la mémoire dans atldbgmem. h.|

### <a name="mfc-trace-flags"></a>Indicateurs de trace MFC

|Catégorie MFC|Description|
|------------------|-----------------|
|`traceAppMsg`|Usage général, les messages MFC. Toujours recommandé.|
|`traceDumpContext`|Messages de [CDumpContext](../../mfc/reference/cdumpcontext-class.md).|
|`traceWinMsg`|Messages du code de gestion des messages de MFC.|
|`traceMemory`|Messages du code de gestion de la mémoire de MFC.|
|`traceCmdRouting`|Messages du code de routage des commandes Windows de MFC.|
|`traceHtml`|Messages de la prise en charge de la boîte de dialogue DHTML de MFC.|
|`traceSocket`|Messages de la prise en charge des sockets MFC.|
|`traceOle`|Messages de la prise en charge OLE de MFC.|
|`traceDatabase`|Messages de la prise en charge des bases de données MFC.|
|`traceInternet`|Messages du support Internet de MFC.|

Pour déclarer une catégorie de trace personnalisée, déclarez une instance globale de la `CTraceCategory` classe comme suit :

[!code-cpp[NVC_ATL_Utilities#109](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_3.cpp)]

Le nom de catégorie, MY_CATEGORY dans cet exemple, est le nom que vous spécifiez pour le paramètre *Category* . Le premier paramètre est le nom de catégorie qui s’affichera dans l’outil de trace ATL/MFC. Le deuxième paramètre est le niveau de trace par défaut. Ce paramètre est facultatif et le niveau de trace par défaut est 0.

Pour utiliser une catégorie définie par l’utilisateur :

[!code-cpp[NVC_ATL_Utilities#110](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_4.cpp)]

Pour spécifier que vous souhaitez filtrer les messages de trace, insérez les définitions de ces macros dans stdafx. h avant l' `#include <atlbase.h>` instruction.

Vous pouvez également définir le filtre dans les directives de préprocesseur de la boîte de dialogue **pages de propriétés** . Cliquez sur l’onglet **préprocesseur** , puis insérez le global dans la zone de modification **définitions de préprocesseur** .

Atlbase. h contient les définitions par défaut des macros ATLTRACE2 et ces définitions seront utilisées si vous ne définissez pas ces symboles avant le traitement de atlbase. h.

Dans les versions release, ATLTRACE2 se compile en `(void) 0` .

ATLTRACE2 limite le contenu de la chaîne à envoyer au périphérique de vidage à 1023 caractères au maximum, après la mise en forme.

ATLTRACE et ATLTRACE2 ont le même comportement, ATLTRACE est inclus à des fins de compatibilité descendante.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#111](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_5.cpp)]

## <a name="see-also"></a>Voir aussi

[Macros](../../atl/reference/atl-macros.md)<br/>
[Fonctions globales de débogage et de rapport d’erreurs](../../atl/reference/debugging-and-error-reporting-global-functions.md)
