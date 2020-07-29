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
ms.openlocfilehash: 823d424620e205d14f247a147bbf7dcb40a626b9
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222912"
---
# <a name="cmemorystate-structure"></a>CMemoryState, structure

Offre un moyen pratique de détecter les fuites de mémoire dans votre programme.

## <a name="syntax"></a>Syntaxe

```
struct CMemoryState
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CMemoryState :: CMemoryState](#cmemorystate)|Construit une structure de type classe qui contrôle les points de contrôle de la mémoire.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CMemoryState :: Checkpoint](#checkpoint)|Obtient un instantané (point de contrôle) de l’état actuel de la mémoire.|
|[CMemoryState ::D ifference](#difference)|Calcule la différence entre deux objets de type `CMemoryState` .|
|[CMemoryState ::D umpAllObjectsSince](#dumpallobjectssince)|Vide un résumé de tous les objets actuellement alloués depuis un point de contrôle précédent.|
|[CMemoryState ::D umpStatistics](#dumpstatistics)|Imprime les statistiques d’allocation de mémoire pour un `CMemoryState` objet.|

## <a name="remarks"></a>Notes

`CMemoryState`est une structure et n’a pas de classe de base.

Une « fuite de mémoire » se produit lorsque la mémoire d’un objet est allouée sur le tas, mais pas libérée lorsqu’elle n’est plus nécessaire. De telles fuites de mémoire peuvent finir par entraîner des erreurs de mémoire insuffisante. Il existe plusieurs façons d’allouer et de libérer de la mémoire dans votre programme :

- Utilisation de la `malloc` /  `free` famille de fonctions à partir de la bibliothèque Runtime.

- À l’aide des fonctions de gestion de la mémoire de l’API Windows, `LocalAlloc` /  `LocalFree` et `GlobalAlloc` /  `GlobalFree` .

- Utilisation des **`new`** opérateurs C++ et **`delete`** .

Les `CMemoryState` Diagnostics permettent uniquement de détecter les fuites de mémoire provoquées lorsque la mémoire allouée à l’aide de l' **`new`** opérateur n’est pas désallouée à l’aide de **`delete`** . Les deux autres groupes de fonctions de gestion de la mémoire sont pour les programmes non-C + +, et il n’est pas recommandé de les mélanger avec **`new`** et **`delete`** dans le même programme. Une macro supplémentaire, DEBUG_NEW, est fournie pour remplacer l' **`new`** opérateur lorsque vous avez besoin d’un suivi des numéros de fichier et de ligne des allocations de mémoire. DEBUG_NEW est utilisé chaque fois que vous utilisez normalement l' **`new`** opérateur.

Comme pour les autres diagnostics, les `CMemoryState` Diagnostics sont disponibles uniquement dans les versions Debug de votre programme. La constante _DEBUG doit être définie pour une version de débogage.

Si vous pensez que votre programme présente une fuite de mémoire, vous pouvez utiliser les `Checkpoint` `Difference` fonctions, et `DumpStatistics` pour découvrir la différence entre l’état de la mémoire (objets alloués) à deux points différents de l’exécution du programme. Ces informations peuvent être utiles pour déterminer si une fonction nettoie tous les objets qu’elle alloue.

Si le simple fait de savoir où le déséquilibre de l’allocation et de la désallocation se produit ne fournit pas suffisamment d’informations, vous pouvez utiliser la `DumpAllObjectsSince` fonction pour vider tous les objets alloués depuis l’appel précédent à `Checkpoint` . Ce dump indique l’ordre d’allocation, le fichier source et la ligne où l’objet a été alloué (si vous utilisez DEBUG_NEW pour l’allocation), ainsi que la dérivation de l’objet, son adresse et sa taille. `DumpAllObjectsSince`appelle également la fonction de chaque objet `Dump` pour fournir des informations sur son état actuel.

Pour plus d’informations sur l’utilisation de `CMemoryState` et d’autres diagnostics, consultez [débogage des applications MFC](/visualstudio/debugger/mfc-debugging-techniques).

> [!NOTE]
> Les déclarations d’objets de type `CMemoryState` et les appels aux fonctions membres doivent être placés entre crochets par les `#if defined(_DEBUG)/#endif` directives. Les diagnostics de la mémoire sont alors inclus uniquement dans les builds de débogage de votre programme.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`CMemoryState`

## <a name="requirements"></a>Spécifications

**En-tête :** AFX. h

## <a name="cmemorystatecheckpoint"></a><a name="checkpoint"></a>CMemoryState :: Checkpoint

Prend un résumé de l’instantané de la mémoire et le stocke dans cet `CMemoryState` objet.

```cpp
void Checkpoint();
```

### <a name="remarks"></a>Notes

Les `CMemoryState` fonctions membres [difference](#difference) et [DumpAllObjectsSince](#dumpallobjectssince) utilisent ces données d’instantané.

### <a name="example"></a>Exemple

  Consultez l’exemple du constructeur [CMemoryState](#cmemorystate) .

## <a name="cmemorystatecmemorystate"></a><a name="cmemorystate"></a>CMemoryState :: CMemoryState

Construit un objet vide `CMemoryState` qui doit être rempli par la fonction membre [Checkpoint](#checkpoint) ou [difference](#difference) .

```
CMemoryState();
```

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_Utilities#18](../../mfc/codesnippet/cpp/cmemorystate-structure_1.cpp)]

## <a name="cmemorystatedifference"></a><a name="difference"></a>CMemoryState ::D ifference

Compare deux `CMemoryState` objets, puis stocke la différence dans cet `CMemoryState` objet.

```
BOOL Difference(
    const CMemoryState& oldState,
    const CMemoryState& newState);
```

### <a name="parameters"></a>Paramètres

*oldState*<br/>
État initial de la mémoire tel que défini par un `CMemoryState` point de contrôle.

*newState*<br/>
Nouvel état de la mémoire tel que défini par un `CMemoryState` point de contrôle.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si les deux États de la mémoire sont différents ; Sinon, 0.

### <a name="remarks"></a>Notes

Un [point de contrôle](#checkpoint) doit avoir été appelé pour chacun des deux paramètres d’état de mémoire.

### <a name="example"></a>Exemple

  Consultez l’exemple du constructeur [CMemoryState](#cmemorystate) .

## <a name="cmemorystatedumpallobjectssince"></a><a name="dumpallobjectssince"></a>CMemoryState ::D umpAllObjectsSince

Appelle la `Dump` fonction pour tous les objets d’un type dérivé de la classe `CObject` qui ont été alloués (et qui sont toujours alloués) depuis le dernier appel de [point de contrôle](#checkpoint) pour cet `CMemoryState` objet.

```cpp
void DumpAllObjectsSince() const;
```

### <a name="remarks"></a>Notes

`DumpAllObjectsSince`L’appel de avec un objet non initialisé `CMemoryState` entraîne le vidage de tous les objets actuellement en mémoire.

### <a name="example"></a>Exemple

  Consultez l’exemple du constructeur [CMemoryState](#cmemorystate) .

## <a name="cmemorystatedumpstatistics"></a><a name="dumpstatistics"></a>CMemoryState ::D umpStatistics

Imprime un rapport de statistiques de mémoire concis à partir d’un `CMemoryState` objet qui est rempli par la fonction membre de [différence](#difference) .

```cpp
void DumpStatistics() const;
```

### <a name="remarks"></a>Notes

Le rapport, qui est imprimé sur l’appareil [afxDump](diagnostic-services.md#afxdump) , présente les éléments suivants :

Un exemple de rapport fournit des informations sur le nombre (ou le montant) de :

- blocs libres

- blocs normaux

- Blocs CRT

- ignorer les blocs

- blocs clients

- mémoire maximale utilisée par le programme à un moment donné (en octets)

- mémoire totale actuellement utilisée par le programme (en octets)

Les blocs libres sont le nombre de blocs dont la désallocation a été différée si `afxMemDF` a la valeur `delayFreeMemDF` . Pour plus d’informations, consultez [afxMemDF](diagnostic-services.md#afxmemdf), dans la section « macros MFC et globales ».

### <a name="example"></a>Exemple

  Le code suivant doit être placé dans *ProjName*App. cpp. Définissez les variables globales suivantes :

[!code-cpp[NVC_MFC_Utilities#40](../../mfc/codesnippet/cpp/cmemorystate-structure_2.cpp)]

Dans la `InitInstance` fonction, ajoutez la ligne :

[!code-cpp[NVC_MFC_Utilities#41](../../mfc/codesnippet/cpp/cmemorystate-structure_3.cpp)]

Ajoutez un gestionnaire pour la `ExitInstance` fonction et utilisez le code suivant :

[!code-cpp[NVC_MFC_Utilities#42](../../mfc/codesnippet/cpp/cmemorystate-structure_4.cpp)]

Vous pouvez maintenant exécuter le programme en mode débogage pour afficher la sortie de la `DumpStatistics` fonction.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)
