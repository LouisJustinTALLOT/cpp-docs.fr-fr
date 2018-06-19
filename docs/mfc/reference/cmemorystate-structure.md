---
title: Structure de CMemoryState | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMemoryState
dev_langs:
- C++
helpviewer_keywords:
- CMemoryState structure [MFC]
- memory leaks [MFC], detecting
- detecting memory leaks [MFC]
ms.assetid: 229d9de7-a6f3-4cc6-805b-5a9d9b1bfe1d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d9dbcaa3f8e02a87713363f1ea38c5d2260171df
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33367969"
---
# <a name="cmemorystate-structure"></a>Structure de CMemoryState
Fournit un moyen pratique pour détecter les fuites de mémoire dans votre programme.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
struct CMemoryState  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CMemoryState::CMemoryState](#cmemorystate)|Construit une structure de classe qui contrôle les points de contrôle de mémoire.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CMemoryState::Checkpoint](#checkpoint)|Obtient un instantané (point de contrôle) de l’état actuel de la mémoire.|  
|[CMemoryState::Difference](#difference)|Calcule la différence entre deux objets de type `CMemoryState`.|  
|[CMemoryState::DumpAllObjectsSince](#dumpallobjectssince)|Exporte un résumé de tous les objets actuellement allouées depuis un point de contrôle précédent.|  
|[CMemoryState::DumpStatistics](#dumpstatistics)|Imprime les statistiques d’allocation de mémoire pour un `CMemoryState` objet.|  
  
## <a name="remarks"></a>Notes  
 `CMemoryState` est une structure et ne dispose pas d’une classe de base.  
  
 Une « fuite de mémoire » se produit lors de la mémoire pour un objet est allouée sur le tas, mais pas libérée lorsqu’il n’est plus nécessaire. Les fuites de mémoire peuvent générer des erreurs de mémoire insuffisante. Il existe plusieurs façons pour allouer et libérer la mémoire dans votre programme :  
  
-   À l’aide de la `malloc` /  **libre** famille de fonctions à partir de la bibliothèque Runtime.  
  
-   Utilisation des fonctions de gestion de mémoire API Windows, **LocalAlloc**/ **LocalFree** et **GlobalAlloc**/ **GlobalFree** .  
  
-   À l’aide de C++ **nouveau** et **supprimer** opérateurs.  
  
 Le `CMemoryState` diagnostics uniquement aider à détecter la mémoire fuites provoqués par la mémoire allouée à l’aide de la **nouveau** opérateur n’est désallouée à l’aide de **supprimer**. Les deux autres groupes de fonctions de gestion de la mémoire sont pour les programmes non-C++ et les combiner avec **nouveau** et **supprimer** dans le même programme n’est pas recommandée. Une macro supplémentaire, `DEBUG_NEW`, est fourni pour remplacer le **nouveau** opérateur lorsque vous avez besoin de fichiers et de suivi du numéro de ligne des allocations de mémoire. `DEBUG_NEW` est utilisé chaque fois que vous utiliseriez normalement le **nouveau** opérateur.  
  
 Comme avec d’autres diagnostics, le `CMemoryState` diagnostics sont disponibles uniquement dans les versions debug de votre programme. Une version de débogage doit avoir le **_DEBUG** constante définie.  
  
 Si vous pensez que votre programme comporte une fuite de mémoire, vous pouvez utiliser la `Checkpoint`, **différence**, et `DumpStatistics` fonctions pour détecter la différence entre l’état de la mémoire (objets alloués) à deux niveaux différents dans un programme exécution. Ces informations peuvent être utiles pour déterminer si une fonction est nettoyage de tous les objets qu’il alloue.  
  
 Si simplement savoir où se produit le déséquilibre de l’allocation et la désallocation ne fournit pas suffisamment d’informations, vous pouvez utiliser la `DumpAllObjectsSince` à vider tous les objets alloués depuis le précédent appel de fonction `Checkpoint`. Ce dump illustre l’ordre d’allocation, le fichier source et la ligne où l’objet a été alloué (si vous utilisez `DEBUG_NEW` pour l’allocation) et la dérivation de l’objet, son adresse et sa taille. `DumpAllObjectsSince` appelle également de chaque objet `Dump` afin de fournir des informations sur son état actuel.  
  
 Pour plus d’informations sur l’utilisation de `CMemoryState` et autres diagnostics, consultez [débogage des Applications MFC](/visualstudio/debugger/mfc-debugging-techniques).  
  
> [!NOTE]
>  Déclarations d’objets de type `CMemoryState` et les appels aux fonctions de membre doivent être encadrées par des `#if defined(_DEBUG)/#endif` directives. Cela provoque des diagnostics de la mémoire être inclus uniquement dans les builds de votre programme de débogage.  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `CMemoryState`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** afx.h  
  
##  <a name="checkpoint"></a>  CMemoryState::Checkpoint  
 Prend un instantané récapitulatif de la mémoire et le stocke dans ce `CMemoryState` objet.  
  
```  
void Checkpoint();
```  
  
### <a name="remarks"></a>Notes  
 Le `CMemoryState` fonctions membres [différence](#difference) et [DumpAllObjectsSince](#dumpallobjectssince) utiliser ces données de capture instantanée.  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de la [CMemoryState](#cmemorystate) constructeur.  
  
##  <a name="cmemorystate"></a>  CMemoryState::CMemoryState  
 Construit un vide `CMemoryState` objet doit être rempli par le [point de contrôle](#checkpoint) ou [différence](#difference) fonction membre.  
  
```  
CMemoryState();
```  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_Utilities#18](../../mfc/codesnippet/cpp/cmemorystate-structure_1.cpp)]  
  
##  <a name="difference"></a>  CMemoryState::Difference  
 Compare deux `CMemoryState` objets, puis stocke la différence dans la collection `CMemoryState` objet.  
  
```  
BOOL Difference(
    const CMemoryState& oldState,   
    const CMemoryState& newState);
```  
  
### <a name="parameters"></a>Paramètres  
 *oldState*  
 L’état de mémoire initiale, comme défini par un `CMemoryState` point de contrôle.  
  
 *newState*  
 Le nouvel état de mémoire, tel que défini par un `CMemoryState` point de contrôle.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si les mémoire de deux États sont différents ; Sinon, 0.  
  
### <a name="remarks"></a>Notes  
 [Point de contrôle](#checkpoint) doit être appelé pour chacun des deux paramètres d’état de la mémoire.  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de la [CMemoryState](#cmemorystate) constructeur.  
  
##  <a name="dumpallobjectssince"></a>  CMemoryState::DumpAllObjectsSince  
 Appelle le `Dump` (fonction) pour tous les objets d’un type dérivé de la classe `CObject` qui ont été alloués (et sont toujours allouées) depuis le dernier [point de contrôle](#checkpoint) appeler pour ce `CMemoryState` objet.  
  
```  
void DumpAllObjectsSince() const;

 
```  
  
### <a name="remarks"></a>Notes  
 Appel de `DumpAllObjectsSince` avec non initialisé `CMemoryState` dump d’objets tous les objets actuellement en mémoire.  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de la [CMemoryState](#cmemorystate) constructeur.  
  
##  <a name="dumpstatistics"></a>  CMemoryState::DumpStatistics  
 Imprime un rapport de statistiques de mémoire concis à partir un `CMemoryState` objet qui est remplie par le [différence](#difference) fonction membre.  
  
```  
void DumpStatistics() const;

 
```  
  
### <a name="remarks"></a>Notes  
 Le rapport, qui est imprimé sur le [afxDump](diagnostic-services.md#afxdump) périphérique, affiche les informations suivantes :  
  
 Un exemple de rapport fournit des informations sur le nombre (ou un montant) de :  
  
-   nombre de blocs libres  
  
-   blocs Normal  
  
-   Blocs CRT  
  
-   Ignorer les blocs  
  
-   blocs clients  
  
-   mémoire maximale utilisée par le programme à tout moment (en octets)  
  
-   quantité totale de mémoire actuellement utilisée par le programme (en octets)  
  
 Les blocs libres sont le nombre de blocs dont la désallocation est différée si `afxMemDF` a été définie sur **delayFreeMemDF**. Pour plus d’informations, consultez [afxMemDF](diagnostic-services.md#afxmemdf), dans la section « MFC Macros et objet Globals ». Consultez [Types de blocs sur le tas de débogage](http://msdn.microsoft.com/en-us/db2e7f62-0679-4b39-a23f-26f2c2f407c5) pour plus d’informations sur ces types de blocs.  
  
### <a name="example"></a>Exemple  
  Le code suivant doit être placé dans *NomProj*App.cpp. Définissez les variables globales suivantes :  
  
 [!code-cpp[NVC_MFC_Utilities#40](../../mfc/codesnippet/cpp/cmemorystate-structure_2.cpp)]  
  
 Dans la `InitInstance` fonctionne, ajoutez la ligne :  
  
 [!code-cpp[NVC_MFC_Utilities#41](../../mfc/codesnippet/cpp/cmemorystate-structure_3.cpp)]  
  
 Ajoutez un gestionnaire pour le `ExitInstance` la fonction et utilisez le code suivant :  
  
 [!code-cpp[NVC_MFC_Utilities#42](../../mfc/codesnippet/cpp/cmemorystate-structure_4.cpp)]  
  
 Vous pouvez maintenant exécuter le programme en mode débogage pour afficher la sortie de la `DumpStatistics` (fonction).  
  
## <a name="see-also"></a>Voir aussi  
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)



