---
title: CMemoryState, structure
ms.date: 11/04/2016
f1_keywords:
- CMemoryState
helpviewer_keywords:
- CMemoryState structure [MFC]
- memory leaks [MFC], detecting
- detecting memory leaks [MFC]
ms.assetid: 229d9de7-a6f3-4cc6-805b-5a9d9b1bfe1d
ms.openlocfilehash: 8f49a9faf70673c62167deeaa1bef33e4882378f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369989"
---
# <a name="cmemorystate-structure"></a>CMemoryState, structure

Fournit un moyen pratique de détecter les fuites de mémoire dans votre programme.

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
|[CMemoryState::Checkpoint](#checkpoint)|Obtient un instantané (point de contrôle) de l’état de mémoire actuel.|
|[CMemoryState::Difference](#difference)|Calcule la différence entre deux `CMemoryState`objets de type .|
|[CMemoryState::DumpAllObjectsSince](#dumpallobjectssince)|Décharge un résumé de tous les objets actuellement alloués depuis un contrôle précédent.|
|[CMemoryState::DumpStatistics](#dumpstatistics)|Imprime les statistiques `CMemoryState` d’allocation de mémoire pour un objet.|

## <a name="remarks"></a>Notes

`CMemoryState`est une structure et n’a pas de classe de base.

Une « fuite de mémoire » se produit lorsque la mémoire d’un objet est allouée sur le tas mais n’est pas deallocée lorsqu’elle n’est plus nécessaire. De telles fuites de mémoire peuvent éventuellement conduire à des erreurs hors mémoire. Il existe plusieurs façons d’allouer et de traiter la mémoire dans votre programme :

- Utilisation `malloc` /  `free` de la famille des fonctions de la bibliothèque de temps d’exécution.

- Utilisation des fonctions de gestion `LocalAlloc` /  `LocalFree` `GlobalAlloc` /  `GlobalFree`de la mémoire De l’API Windows, et .

- Utilisation des **nouveaux** opérateurs et **suppressions** de CMD.

Les `CMemoryState` diagnostics ne font qu’aider à détecter les fuites de mémoire causées lorsque la mémoire allouée à l’aide du **nouvel** opérateur n’est pas deallocated à l’aide **de supprimer**. Les deux autres groupes de fonctions de gestion de la mémoire sont pour les programmes non-CMD, et il n’est pas recommandé de les mélanger avec **des nouveaux** et **des suppressions** dans le même programme. Une macro supplémentaire, DEBUG_NEW, est fournie pour remplacer le **nouvel** opérateur lorsque vous avez besoin de suivi des fichiers et des numéros de ligne des allocations de mémoire. DEBUG_NEW est utilisé chaque fois que vous utilisez normalement le **nouvel** opérateur.

Comme pour d’autres `CMemoryState` diagnostics, les diagnostics ne sont disponibles que dans les versions de déboise de votre programme. Une version débogéine doit avoir la _DEBUG constante définie.

Si vous soupçonnez que votre programme a `Checkpoint` `Difference`une `DumpStatistics` fuite de mémoire, vous pouvez utiliser le , , et fonctionne pour découvrir la différence entre l’état de mémoire (objets alloués) à deux points différents dans l’exécution du programme. Ces informations peuvent être utiles pour déterminer si une fonction nettoie tous les objets qu’elle attribue.

Si le simple fait de savoir où se produit le déséquilibre `DumpAllObjectsSince` dans l’attribution et la transaction `Checkpoint`ne fournit pas suffisamment d’informations, vous pouvez utiliser la fonction pour vider tous les objets alloués depuis l’appel précédent à . Ce dépotoir montre l’ordre d’attribution, le fichier source et la ligne où l’objet a été attribué (si vous utilisez DEBUG_NEW pour l’allocation), et la dérivation de l’objet, son adresse, et sa taille. `DumpAllObjectsSince`appelle également la `Dump` fonction de chaque objet pour fournir des informations sur son état actuel.

Pour plus d’informations `CMemoryState` sur la façon d’utiliser et d’autres diagnostics, voir [Debugging MFC Applications](/visualstudio/debugger/mfc-debugging-techniques).

> [!NOTE]
> Les déclarations d’objets de type `CMemoryState` et les `#if defined(_DEBUG)/#endif` appels aux fonctions des membres doivent être entre crochets par des directives. Cela provoque des diagnostics de mémoire d’être inclus uniquement dans les constructions de débogage de votre programme.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`CMemoryState`

## <a name="requirements"></a>Spécifications

**En-tête:** afx.h

## <a name="cmemorystatecheckpoint"></a><a name="checkpoint"></a>CMemoryState::Checkpoint

Prend un résumé instantané de la `CMemoryState` mémoire et le stocke dans cet objet.

```
void Checkpoint();
```

### <a name="remarks"></a>Notes

Le `CMemoryState` membre fonctionne [Différence](#difference) et [DumpAllObjectsSince](#dumpallobjectssince) utiliser ces données instantanées.

### <a name="example"></a>Exemple

  Voir l’exemple pour le constructeur [CMemoryState.](#cmemorystate)

## <a name="cmemorystatecmemorystate"></a><a name="cmemorystate"></a>CMemoryState::CMemoryState

Construit un `CMemoryState` objet vide qui doit être rempli par la fonction [de membre Checkpoint](#checkpoint) ou [Différence.](#difference)

```
CMemoryState();
```

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_Utilities#18](../../mfc/codesnippet/cpp/cmemorystate-structure_1.cpp)]

## <a name="cmemorystatedifference"></a><a name="difference"></a>CMemoryState::Difference

Compare deux `CMemoryState` objets, puis stocke `CMemoryState` la différence dans cet objet.

```
BOOL Difference(
    const CMemoryState& oldState,
    const CMemoryState& newState);
```

### <a name="parameters"></a>Paramètres

*oldState*<br/>
L’état de mémoire `CMemoryState` initial tel que défini par un point de contrôle.

*newState*<br/>
Le nouvel état de `CMemoryState` mémoire tel que défini par un point de contrôle.

### <a name="return-value"></a>Valeur de retour

Nonzero si les deux états de mémoire sont différents; sinon 0.

### <a name="remarks"></a>Notes

[Checkpoint](#checkpoint) doit avoir été appelé pour chacun des deux paramètres de l’état de mémoire.

### <a name="example"></a>Exemple

  Voir l’exemple pour le constructeur [CMemoryState.](#cmemorystate)

## <a name="cmemorystatedumpallobjectssince"></a><a name="dumpallobjectssince"></a>CMemoryState::DumpAllObjectsSince

Appelle `Dump` la fonction pour tous les `CObject` objets d’un type dérivé de la classe qui `CMemoryState` ont été alloués (et sont toujours alloués) depuis le dernier appel [Checkpoint](#checkpoint) pour cet objet.

```
void DumpAllObjectsSince() const;
```

### <a name="remarks"></a>Notes

Appeler `DumpAllObjectsSince` avec un objet `CMemoryState` uninitialisé va déverser tous les objets actuellement en mémoire.

### <a name="example"></a>Exemple

  Voir l’exemple pour le constructeur [CMemoryState.](#cmemorystate)

## <a name="cmemorystatedumpstatistics"></a><a name="dumpstatistics"></a>CMemoryState::DumpStatistics

Imprime un rapport concis `CMemoryState` de statistiques de mémoire à partir d’un objet qui est rempli par la fonction de membre [de différence.](#difference)

```
void DumpStatistics() const;
```

### <a name="remarks"></a>Notes

Le rapport, qui est imprimé sur l’appareil [afxDump,](diagnostic-services.md#afxdump) montre ce qui suit :

Un rapport d’échantillon donne des informations sur le nombre (ou le montant) des :

- blocs gratuits

- blocs normaux

- Blocs CRT

- ignorer les blocs

- blocs clients

- mémoire maximale utilisée par le programme à tout moment (dans les octets)

- mémoire totale actuellement utilisée par le programme (dans les octets)

Les blocs libres sont le nombre de `afxMemDF` blocs dont `delayFreeMemDF`l’accord a été retardé si elle a été fixée à . Pour plus d’informations, voir [afxMemDF](diagnostic-services.md#afxmemdf), dans la section "MFC Macros and Globals".

### <a name="example"></a>Exemple

  Le code suivant doit être placé dans *projname*App.cpp. Définir les variables globales suivantes :

[!code-cpp[NVC_MFC_Utilities#40](../../mfc/codesnippet/cpp/cmemorystate-structure_2.cpp)]

Dans `InitInstance` la fonction, ajoutez la ligne :

[!code-cpp[NVC_MFC_Utilities#41](../../mfc/codesnippet/cpp/cmemorystate-structure_3.cpp)]

Ajouter un gestionnaire `ExitInstance` pour la fonction et utiliser le code suivant :

[!code-cpp[NVC_MFC_Utilities#42](../../mfc/codesnippet/cpp/cmemorystate-structure_4.cpp)]

Vous pouvez maintenant exécuter le programme en mode Debug pour voir la sortie de la `DumpStatistics` fonction.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)
