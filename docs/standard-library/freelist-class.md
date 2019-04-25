---
title: freelist, classe
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::freelist
- allocators/stdext::freelist::pop
- allocators/stdext::freelist::push
helpviewer_keywords:
- stdext::freelist
- stdext::freelist [C++], pop
- stdext::freelist [C++], push
ms.assetid: 8ad7e35c-4c80-4479-8ede-1a2497b06d71
ms.openlocfilehash: ef1f2e617e93869a1084dc030c6496c819f1ed96
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62159390"
---
# <a name="freelist-class"></a>freelist, classe

Gère une liste de blocs de mémoire.

## <a name="syntax"></a>Syntaxe

```cpp
template <std::size_t Sz, class Max>
class freelist : public Max
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*Sz*|Nombre d’éléments du tableau à allouer.|
|*Max*|Classe max représentant le nombre maximal d’éléments à stocker dans la liste de libération. La classe max peut être [max_none](../standard-library/max-none-class.md), [max_unbounded](../standard-library/max-unbounded-class.md), [max_fixed_size](../standard-library/max-fixed-size-class.md) ou[max_variable_size](../standard-library/max-variable-size-class.md).|

## <a name="remarks"></a>Notes

Cette classe de modèle gère une liste de blocs de mémoire de taille *Sz* avec la longueur maximale de la liste déterminée par la classe max passée dans *Max*.

### <a name="constructors"></a>Constructeurs

|Constructeur|Description|
|-|-|
|[freelist](#freelist)|Construit un objet de type `freelist`.|

### <a name="member-functions"></a>Fonctions membres

|Fonction membre|Description|
|-|-|
|[pop](#pop)|Supprime le premier bloc de mémoire de la liste de libération.|
|[push](#push)|Ajoute un bloc de mémoire à la liste.|

## <a name="requirements"></a>Configuration requise

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

La fonction membre retourne NULL si la liste est vide. Sinon, elle supprime le premier bloc de mémoire de la liste.

## <a name="push"></a>  freelist::push

Ajoute un bloc de mémoire à la liste.

```cpp
bool push(void* ptr);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*ptr*|Pointeur vers le bloc de mémoire à ajouter à la liste de libération.|

### <a name="return-value"></a>Valeur de retour

**true** si le `full` fonction de la classe max retourne **false**; sinon, le `push` fonction renvoie **false**.

### <a name="remarks"></a>Notes

Si le `full` fonction de la classe max retourne **false**, cette fonction membre ajoute le bloc de mémoire vers lequel pointé *ptr* au début de la liste.

## <a name="see-also"></a>Voir aussi

[\<allocators>](../standard-library/allocators-header.md)<br/>
