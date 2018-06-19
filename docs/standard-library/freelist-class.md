---
title: freelist, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- allocators/stdext::freelist
- allocators/stdext::freelist::pop
- allocators/stdext::freelist::push
dev_langs:
- C++
helpviewer_keywords:
- stdext::freelist
- stdext::freelist [C++], pop
- stdext::freelist [C++], push
ms.assetid: 8ad7e35c-4c80-4479-8ede-1a2497b06d71
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7e9a8bf702f4373040a6f7255d67f551b5dbfa60
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33846959"
---
# <a name="freelist-class"></a>freelist, classe

Gère une liste de blocs de mémoire.

## <a name="syntax"></a>Syntaxe

```cpp
template <std::size_t Sz, class Max>
class freelist
 : public Max
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|`Sz`|Nombre d’éléments du tableau à allouer.|
|`Max`|Classe max représentant le nombre maximal d’éléments à stocker dans la liste de libération. La classe max peut être [max_none](../standard-library/max-none-class.md), [max_unbounded](../standard-library/max-unbounded-class.md), [max_fixed_size](../standard-library/max-fixed-size-class.md) ou[max_variable_size](../standard-library/max-variable-size-class.md).|

## <a name="remarks"></a>Notes

Cette classe de modèle gère une liste de blocs de mémoire de taille `Sz` avec la longueur maximale de la liste déterminée par la classe max passée dans `Max`.

### <a name="constructors"></a>Constructeurs

|Constructeur|Description|
|-|-|
|[freelist](#freelist)|Construit un objet de type `freelist`.|

### <a name="member-functions"></a>Fonctions membres

|Fonction membre|Description|
|-|-|
|[pop](#pop)|Supprime le premier bloc de mémoire de la liste de libération.|
|[push](#push)|Ajoute un bloc de mémoire à la liste.|

## <a name="requirements"></a>Spécifications

**En-tête :** \<allocators>

**Espace de noms :** stdext

## <a name="freelist"></a>  freelist::freelist

Construit un objet de type `freelist`.

```cpp
freelist();
```

### <a name="remarks"></a>Notes

## <a name="pop"></a>  freelist::pop

Supprime le premier bloc de mémoire de la liste de libération.

```cpp
void *pop();
```

### <a name="return-value"></a>Valeur de retour

Retourne un pointeur vers le bloc de mémoire supprimé de la liste.

### <a name="remarks"></a>Notes

La fonction membre retourne `NULL` si la liste est vide. Sinon, elle supprime le premier bloc de mémoire de la liste.

## <a name="push"></a>  freelist::push

Ajoute un bloc de mémoire à la liste.

```cpp
bool push(void* ptr);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|`ptr`|Pointeur vers le bloc de mémoire à ajouter à la liste de libération.|

### <a name="return-value"></a>Valeur de retour

`true` si la fonction `full` de la classe max retourne `false` ; sinon, la fonction `push` retourne `false`.

### <a name="remarks"></a>Notes

Si la fonction `full` de la classe max retourne `false`, cette fonction membre ajoute le bloc de mémoire désigné par `ptr` au début de la liste.

## <a name="see-also"></a>Voir aussi

[\<allocators>](../standard-library/allocators-header.md)<br/>
