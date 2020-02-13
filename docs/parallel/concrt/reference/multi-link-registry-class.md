---
title: multi_link_registry, classe
ms.date: 11/04/2016
f1_keywords:
- multi_link_registry
- AGENTS/concurrency::multi_link_registry
- AGENTS/concurrency::multi_link_registry::multi_link_registry
- AGENTS/concurrency::multi_link_registry::add
- AGENTS/concurrency::multi_link_registry::begin
- AGENTS/concurrency::multi_link_registry::contains
- AGENTS/concurrency::multi_link_registry::count
- AGENTS/concurrency::multi_link_registry::remove
- AGENTS/concurrency::multi_link_registry::set_bound
helpviewer_keywords:
- multi_link_registry class
ms.assetid: b2aa73a8-e8a6-4255-b117-d07530c328b2
ms.openlocfilehash: e22df5ee65d0219a46065044385dca46aac297a3
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142374"
---
# <a name="multi_link_registry-class"></a>multi_link_registry, classe

L'objet `multi_link_registry` est un `network_link_registry` qui gère plusieurs blocs sources ou plusieurs blocs cibles.

## <a name="syntax"></a>Syntaxe

```cpp
template<class _Block>
class multi_link_registry : public network_link_registry<_Block>;
```

### <a name="parameters"></a>Paramètres

*_Block*<br/>
Type de données de bloc stocké dans l’objet `multi_link_registry`.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Name|Description|
|----------|-----------------|
|[multi_link_registry](#ctor)|Construit un objet `multi_link_registry`.|
|[Destructeur ~ multi_link_registry](#dtor)|Détruit l’objet `multi_link_registry`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Name|Description|
|----------|-----------------|
|[add](#add)|Ajoute un lien à l’objet `multi_link_registry`. (Substitue [network_link_registry :: Add](network-link-registry-class.md#add).)|
|[begin](#begin)|Retourne un itérateur au premier élément de l’objet `multi_link_registry`. (Substitue [network_link_registry :: Begin](network-link-registry-class.md#begin).)|
|[contains](#contains)|Recherche un bloc spécifié dans l’objet `multi_link_registry`. (Substitue [network_link_registry :: Contains](network-link-registry-class.md#contains).)|
|[count](#count)|Compte le nombre d’éléments dans l’objet `multi_link_registry`. (Substitue [network_link_registry :: Count](network-link-registry-class.md#count).)|
|[remove](#remove)|Supprime un lien de l’objet `multi_link_registry`. (Substitue [network_link_registry :: Remove](network-link-registry-class.md#remove).)|
|[set_bound](#set_bound)|Définit une limite supérieure du nombre de liens que l’objet `multi_link_registry` peut contenir.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[network_link_registry](network-link-registry-class.md)

`multi_link_registry`

## <a name="requirements"></a>Spécifications

**En-tête :** agents.h

**Espace de noms :** concurrency

## <a name="add"></a>complémentaires

Ajoute un lien à l’objet `multi_link_registry`.

```cpp
virtual void add(_EType _Link);
```

### <a name="parameters"></a>Paramètres

*_Link*<br/>
Pointeur vers un bloc à ajouter.

### <a name="remarks"></a>Notes

La méthode lève une exception [invalid_link_target](invalid-link-target-class.md) si le lien est déjà présent dans le registre, ou si une limite a déjà été définie avec la fonction `set_bound` et qu’un lien a été supprimé.

## <a name="begin"></a>commencer

Retourne un itérateur au premier élément de l’objet `multi_link_registry`.

```cpp
virtual iterator begin();
```

### <a name="return-value"></a>Valeur de retour

Itérateur qui traite le premier élément de l’objet `multi_link_registry`.

### <a name="remarks"></a>Notes

L’état final est indiqué par un lien `NULL`.

## <a name="contains"></a>comprend

Recherche un bloc spécifié dans l’objet `multi_link_registry`.

```cpp
virtual bool contains(_EType _Link);
```

### <a name="parameters"></a>Paramètres

*_Link*<br/>
Pointeur vers un bloc qui doit être recherché dans l’objet `multi_link_registry`.

### <a name="return-value"></a>Valeur de retour

**true** si le bloc spécifié a été trouvé ; sinon, **false** .

## <a name="count"></a>saut

Compte le nombre d’éléments dans l’objet `multi_link_registry`.

```cpp
virtual size_t count();
```

### <a name="return-value"></a>Valeur de retour

Nombre d'éléments de l'objet `multi_link_registry`.

## <a name="ctor"></a>multi_link_registry

Construit un objet `multi_link_registry`.

```cpp
multi_link_registry();
```

## <a name="dtor"></a>~ multi_link_registry

Détruit l’objet `multi_link_registry`.

```cpp
virtual ~multi_link_registry();
```

### <a name="remarks"></a>Notes

La méthode lève une exception [invalid_operation](invalid-operation-class.md) si elle est appelée avant la suppression de tous les liens.

## <a name="remove"></a>Installez

Supprime un lien de l’objet `multi_link_registry`.

```cpp
virtual bool remove(_EType _Link);
```

### <a name="parameters"></a>Paramètres

*_Link*<br/>
Pointeur vers un bloc à supprimer, s’il est trouvé.

### <a name="return-value"></a>Valeur de retour

**true** si le lien a été trouvé et supprimé ; sinon, **false** .

## <a name="set_bound"></a>set_bound

Définit une limite supérieure du nombre de liens que l’objet `multi_link_registry` peut contenir.

```cpp
void set_bound(size_t _MaxLinks);
```

### <a name="parameters"></a>Paramètres

*_MaxLinks*<br/>
Nombre maximal de liens que l’objet `multi_link_registry` peut contenir.

### <a name="remarks"></a>Notes

Une fois qu’une limite est définie, la dissociation d’une entrée amène l’objet `multi_link_registry` à entrer dans un état immuable où d’autres appels à `add` lèvera une exception `invalid_link_target`.

## <a name="see-also"></a>Voir aussi

[accès concurrentiel Namespace](concurrency-namespace.md)<br/>
[single_link_registry, classe](single-link-registry-class.md)
