---
title: Macros de débogage et de rapport d’erreurs | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atldef/ATL::_ATL_DEBUG_INTERFACES
- atldef/ATL::_ATL_DEBUG_QI
- atldef/ATL::ATLASSERT
- afx/ATL::ATLENSURE
- atltrace/ATL::ATLTRACENOTIMPL
- atltrace/ATL::ATLTRACE
dev_langs:
- C++
helpviewer_keywords:
- macros, error reporting
ms.assetid: 4da9b87f-ec5c-4a32-ab93-637780909b9d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b99147c9eb9a331d7cc0f9064b858979d00e2804
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="debugging-and-error-reporting-macros"></a>Macros de débogage et de rapport d’erreurs
Ces macros fournissent des fonctionnalités de débogage et le traçage utiles.  
  
|||  
|-|-|  
|[_ATL_DEBUG_INTERFACES](#_atl_debug_interfaces)|Écrit dans la fenêtre Sortie, n’importe quelle interface fuites qui sont détectés lorsque `_Module.Term` est appelée.|  
|[_ATL_DEBUG_QI](#_atl_debug_qi)|Écrit tous les appels à `QueryInterface` dans la fenêtre Sortie.|  
|[ATLASSERT](#atlassert)|Effectue les mêmes fonctionnalités que le [_ASSERTE](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) macro trouvé dans la bibliothèque Runtime C.|  
|[ATLENSURE](#atlensure)|Effectue une validation des paramètres. Appeler `AtlThrow` si nécessaire|  
|[ATLTRACENOTIMPL](#atltracenotimpl)|Envoie un message à l’unité de vidage que la fonction spécifiée n’est pas implémentée.|  
|[ATLTRACE](#alttrace)|Signale des avertissements pour un périphérique de sortie, tels que la fenêtre du débogueur, selon les indicateurs indiqués et les niveaux. Inclus pour la compatibilité descendante.|  
|[ATLTRACE2](#atltrace2)|Signale des avertissements pour un périphérique de sortie, tels que la fenêtre du débogueur, selon les indicateurs indiqués et les niveaux.|  
  
##  <a name="_atl_debug_interfaces"></a>  _ATL_DEBUG_INTERFACES  
 Définir cette macro avant d’inclure tous les fichiers d’en-tête ATL pour suivre toutes les `AddRef` et **version** appelle sur les interfaces de vos composants dans la fenêtre Sortie.  
  
```
#define _ATL_DEBUG_INTERFACES
```  
  
### <a name="remarks"></a>Notes  
 La sortie de trace s’affichent comme illustré ci-dessous :  
  
 `ATL: QIThunk - 2008         AddRef  :   Object = 0x00d81ba0   Refcount = 1   CBug - IBug`  
  
 La première partie de chaque trace sera toujours `ATL: QIThunk`. L’élément suivant est une valeur qui identifie le notamment *interface thunk* utilisé. Une conversion de code d’interface est un objet utilisé pour conserver un décompte de références et fournir la fonctionnalité de suivi utilisée ici. Une conversion de code nouvelle interface est créée à chaque appel à `QueryInterface` à l’exception des demandes pour le **IUnknown** interface (dans ce cas, le même thunk est renvoyé un chaque fois pour se conformer aux règles d’identité de COM).  
  
 Ensuite, vous verrez `AddRef` ou **version** indiquant quelle méthode a été appelée. Après cela, vous verrez une valeur qui identifie l’objet dont le nombre de référence interface a été modifié. La valeur de suivi est le **cela** pointeur de l’objet.  
  
 Le nombre de références faisant l’objet est le nombre de références sur ce thunk après `AddRef` ou **version** a été appelée. Notez que ce nombre de références peut correspondre pas au nombre de références de l’objet. Chaque thunk conserve son propre comptage des références pour vous aider à respecter les règles de décompte de COM.  
  
 La dernière partie des informations de suivi est le nom de l’objet et l’interface soient affectés par la `AddRef` ou **version** appeler.  
  
 N’importe quelle interface fuites détectées lorsque le serveur s’arrête et `_Module.Term` est appelée va être connecté comme suit :  
  
 `ATL: QIThunk - 2005         LEAK    :   Object = 0x00d81ca0   Refcount = 1   MaxRefCount = 1   CBug - IBug`  
  
 Les informations fournies ici est directement mappée à celles fournies dans les instructions de trace précédente, afin de pouvoir examiner les décomptes de références tout au long de la durée de vie entier d’une conversion de code d’interface. En outre, vous obtenez une indication du nombre maximal de références sur ce thunk interface.  
  
> [!NOTE]
> `_ATL_DEBUG_INTERFACES` peut être utilisé dans les versions commerciales.  
  
##  <a name="_atl_debug_qi"></a>  _ATL_DEBUG_QI  
 Écrit tous les appels à `QueryInterface` dans la fenêtre Sortie.  
  
```
#define _ATL_DEBUG_QI
```  
  
### <a name="remarks"></a>Notes  
 Si un appel à `QueryInterface` a échoué, la fenêtre Sortie affiche :  
  
 *nom de l’interface* - `failed`  
  
##  <a name="atlassert"></a>  ATLASSERT  
 Le `ATLASSERT` macro effectue les mêmes fonctionnalités que le [_ASSERTE](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) macro trouvé dans la bibliothèque Runtime C.  
  
```
ATLASSERT(booleanExpression);
```  
  
### <a name="parameters"></a>Paramètres  
 `booleanExpression`  
 Expression (pointeurs inclus) qui prend une valeur différente de zéro ou 0.  
  
### <a name="remarks"></a>Notes  
 Dans les versions debug, `ATLASSERT` prend la valeur `booleanExpression` et génère un rapport de débogage lorsque le résultat est false.  

## <a name="requirements"></a>Spécifications  
 **En-tête :** atldef.h  
    
##  <a name="atlensure"></a>  ATLENSURE  
 Cette macro est utilisée pour valider les paramètres passés à une fonction.  
  
```
ATLENSURE(booleanExpression);
ATLENSURE_THROW(booleanExpression, hr);
```  
  
### <a name="parameters"></a>Paramètres  
 `booleanExpression`  
 Spécifie une expression booléenne à tester.  
  
 `hr`  
 Spécifie un code d’erreur à retourner.  
  
### <a name="remarks"></a>Notes  
 Ces macros fournissent un mécanisme permettant de détecter et d’avertir l’utilisateur de l’utilisation des paramètres incorrects.  
  
 Les appels de macro `ATLASSERT` et si la condition échoue appels `AtlThrow`.  
  
 Dans le **ATLENSURE** cas, `AtlThrow` est appelée avec E_FAIL.  
  
 Dans le **ATLENSURE_THROW** cas, `AtlThrow` est appelée avec la valeur HRESULT spécifiée.  
  
 La différence entre **ATLENSURE** et `ATLASSERT` qui est **ATLENSURE** lève une exception dans la version builds ainsi que dans les versions Debug.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_ATL_Utilities#108](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_1.cpp)]  

## <a name="requirements"></a>Spécifications  
 **En-tête :** afx.h  

##  <a name="atltracenotimpl"></a>  ATLTRACENOTIMPL  
 Dans les versions debug de ATL, envoie la chaîne « `funcname` n’est pas implémentée » pour l’unité de sauvegarde et la retourne **E_NOTIMPL**.  
  
```
ATLTRACENOTIMPL(funcname);
```  
  
### <a name="parameters"></a>Paramètres  
 `funcname`  
 [in] Chaîne contenant le nom de la fonction qui n’est pas implémentée.  
  
### <a name="remarks"></a>Notes  
 Dans les versions release, retourne simplement **E_NOTIMPL**.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_ATL_Utilities#127](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_2.cpp)]  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atltrace.h 

##  <a name="atltrace"></a>  ATLTRACE
 Signale des avertissements pour un périphérique de sortie, tels que la fenêtre du débogueur, selon les indicateurs indiqués et les niveaux. Inclus pour la compatibilité descendante.  
  
```
ATLTRACE(exp);

ATLTRACE(  
    DWORD category,
    UINT  level,
    LPCSTR lpszFormat, ...);
```  
  
### <a name="parameters"></a>Paramètres  
 `exp`  
 [in] La chaîne et les variables à envoyer à la fenêtre de sortie de Visual C++ ou toute application qui intercepte ces messages.  
  
 `category`  
 [in] Type d’événement ou une méthode sur lequel au rapport. Consultez les notes pour obtenir la liste des catégories.  
  
 `level`  
 [in] Le niveau de suivi pour le rapport. Consultez la section Notes pour plus d’informations.  
  
 `lpszFormat`  
 [in] La chaîne mise en forme à envoyer à l’unité de vidage.  
  
### <a name="remarks"></a>Notes  
 Consultez [ATLTRACE2](#atltrace2) pour obtenir une description de **ATLTRACE**. **ATLTRACE** et `ATLTRACE2` ont le même comportement, **ATLTRACE** est inclus pour la compatibilité descendante.  
  
##  <a name="atltrace2"></a>  ATLTRACE2  
 Signale des avertissements pour un périphérique de sortie, tels que la fenêtre du débogueur, selon les indicateurs indiqués et les niveaux.  
  
```
ATLTRACE2(exp);

ATLTRACE2(
    DWORD category,
    UINT level,
    LPCSTRlpszFormat,  ...);
```  
  
### <a name="parameters"></a>Paramètres  
 `exp`  
 [in] Chaîne à envoyer à la fenêtre de sortie de Visual C++ ou toute application qui intercepte ces messages.  
  
 `category`  
 [in] Type d’événement ou une méthode sur lequel au rapport. Consultez les notes pour obtenir la liste des catégories.  
  
 `level`  
 [in] Le niveau de suivi pour le rapport. Consultez la section Notes pour plus d’informations.  
  
 `lpszFormat`  
 [in] Le `printf`-style de chaîne de format à utiliser pour créer une chaîne à envoyer à l’unité de vidage.  
  
### <a name="remarks"></a>Notes  
 La forme abrégée de `ATLTRACE2` écrit une chaîne dans le débogueur de sortie de fenêtre. La deuxième forme de `ATLTRACE2` également écrit la sortie dans la fenêtre de sortie du débogueur, mais peut être les paramètres de l’ATL/MFC Trace Tool (consultez [ATLTraceTool, exemple](../../visual-cpp-samples.md)). Par exemple, si vous définissez `level` à 4 et la ATL/MFC Trace Tool au niveau 0, vous ne verrez pas le message. *niveau* peut être 0, 1, 2, 3 ou 4. Les rapports par défaut, 0, seuls les problèmes plus sérieux.  
  
 Le `category` paramètre répertorie les indicateurs de trace à définir. Ces indicateurs correspondent aux types des méthodes pour lequel vous souhaitez effectuer un rapport. Les tableaux ci-dessous répertorient les indicateurs de trace valide que vous pouvez utiliser pour la `category` paramètre.  
  
### <a name="atl-trace-flags"></a>Indicateurs de Trace ATL  
  
|Catégorie d’ATL|Description|  
|------------------|-----------------|  
|`atlTraceGeneral`|Rapports sur toutes les applications ATL. Valeur par défaut.|  
|`atlTraceCOM`|Rapports sur les méthodes COM.|  
|`atlTraceQI`|Rapports sur les appels QueryInterface.|  
|`atlTraceRegistrar`|Rapports sur l’enregistrement des objets.|  
|`atlTraceRefcount`|Rapports sur la modification du nombre de références.|  
|`atlTraceWindowing`|Rapports sur les méthodes windows ; par exemple, indique un ID de mappage de message non valide.|  
|`atlTraceControls`|Rapports sur les contrôles ; par exemple, des rapports quand un contrôle ou sa fenêtre est détruite.|  
|`atlTraceHosting`|Rapports qui héberge les messages ; rapports, par exemple, lorsqu’un client dans un conteneur est activé.|  
|`atlTraceDBClient`|Rapports sur les modèles de consommateur OLE DB ; par exemple, lorsqu’un appel à GetData échoue, la sortie peut contenir la valeur HRESULT.|  
|`atlTraceDBProvider`|Rapports sur le modèle de fournisseur OLE DB ; par exemple, indique si la création d’une colonne a échoué.|  
|`atlTraceSnapin`|Rapports pour l’application du composant logiciel enfichable MMC.|  
|`atlTraceNotImpl`|Indique que la fonction indiquée n’est pas implémentée.|  
|**atlTraceAllocation**|Retourne les messages imprimés par la mémoire, outils de débogage dans atldbgmem.h.|  
  
### <a name="mfc-trace-flags"></a>Indicateurs de Trace MFC  
  
|Catégorie MFC|Description|  
|------------------|-----------------|  
|**traceAppMsg**|Usage général, les messages MFC. Toujours recommandée.|  
|**traceDumpContext**|Les messages provenant de [CDumpContext](../../mfc/reference/cdumpcontext-class.md).|  
|**traceWinMsg**|Messages de code de gestion de messages MFC.|  
|**traceMemory**|Messages à partir du code de gestion de mémoire de MFC.|  
|**traceCmdRouting**|Code de routage de commande de messages à partir Windows de MFC.|  
|**traceHtml**|Messages de la prise en charge de la boîte de dialogue MFC DHTML.|  
|**traceSocket**|Messages de la prise en charge du socket de MFC.|  
|**traceOle**|Messages de la prise en charge MFC OLE.|  
|**traceDatabase**|Messages de la prise en charge de la base de données MFC.|  
|**traceInternet**|Prend en charge des messages à partir d’Internet MFC.|  
  
 Pour déclarer une catégorie de suivi personnalisé, déclarez une instance globale de la `CTraceCategory` classe comme suit :  
  
 [!code-cpp[NVC_ATL_Utilities#109](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_3.cpp)]  
  
 Le nom de catégorie, `MY_CATEGORY` dans cet exemple, est le nom que vous spécifiez pour le `category` paramètre. Le premier paramètre est le nom de catégorie qui apparaîtra dans les ATL/MFC Trace Tool. Le deuxième paramètre est le niveau de trace par défaut. Ce paramètre est facultatif, et le niveau de trace par défaut est 0.  
  
 Pour utiliser une catégorie définie par l’utilisateur :  
  
 [!code-cpp[NVC_ATL_Utilities#110](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_4.cpp)]  
  
 Pour spécifier que vous souhaitez filtrer les messages de trace, insérez les définitions de ces macros dans Stdafx.h avant la `#include <atlbase.h>` instruction.  
  
 Vous pouvez également définir le filtre dans les directives de préprocesseur dans le **Pages de propriétés** boîte de dialogue. Cliquez sur le **préprocesseur** onglet, puis insérez globale dans le **définitions de préprocesseur** zone d’édition.  
  
 Atlbase.h contient des définitions par défaut de la `ATLTRACE2` macros et ces définitions seront utilisées si vous ne définissez pas ces symboles avant le traitement de atlbase.h.  
  
 Dans les versions release, `ATLTRACE2` est compilé en `(void) 0`.  
  
 `ATLTRACE2` limite la valeur de la chaîne à envoyer à l’unité de vidage à ne plus de 1023 caractères, après la mise en forme.  
  
 **ATLTRACE** et `ATLTRACE2` ont le même comportement, **ATLTRACE** est inclus pour la compatibilité descendante.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_ATL_Utilities#111](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_5.cpp)]  
  
## <a name="see-also"></a>Voir aussi  
 [Macros](../../atl/reference/atl-macros.md)   
 [Fonctions globales de signalement d’erreurs et de débogage](../../atl/reference/debugging-and-error-reporting-global-functions.md)
