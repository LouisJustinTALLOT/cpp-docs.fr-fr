---
description: 'En savoir plus sur : classe multi_link_registry'
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
ms.openlocfilehash: a5d5e6c7e837f76a422c3f2879f74d1af36d64d6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97202130"
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
Type de données de bloc stocké dans l' `multi_link_registry` objet.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[multi_link_registry](#ctor)|Construit un objet `multi_link_registry`.|
|[Destructeur ~ multi_link_registry](#dtor)|Détruit l' `multi_link_registry` objet.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[add](#add)|Ajoute un lien à l' `multi_link_registry` objet. (Substitue [network_link_registry :: Add](network-link-registry-class.md#add).)|
|[commencer](#begin)|Retourne un itérateur au premier élément de l' `multi_link_registry` objet. (Substitue [network_link_registry :: Begin](network-link-registry-class.md#begin).)|
|[contains](#contains)|Recherche `multi_link_registry` un bloc spécifié dans l’objet. (Substitue [network_link_registry :: Contains](network-link-registry-class.md#contains).)|
|[count](#count)|Compte le nombre d’éléments dans l' `multi_link_registry` objet. (Substitue [network_link_registry :: Count](network-link-registry-class.md#count).)|
|[remove](#remove)|Supprime un lien de l' `multi_link_registry` objet. (Substitue [network_link_registry :: Remove](network-link-registry-class.md#remove).)|
|[set_bound](#set_bound)|Définit une limite supérieure du nombre de liens que l' `multi_link_registry` objet peut contenir.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[network_link_registry](network-link-registry-class.md)

`multi_link_registry`

## <a name="requirements"></a>Spécifications

**En-tête :** agents.h

**Espace de noms :** concurrence

## <a name="add"></a><a name="add"></a> complémentaires

Ajoute un lien à l' `multi_link_registry` objet.

```cpp
virtual void add(_EType _Link);
```

### <a name="parameters"></a>Paramètres

*_Link*<br/>
Pointeur vers un bloc à ajouter.

### <a name="remarks"></a>Notes

La méthode lève une exception [invalid_link_target](invalid-link-target-class.md) si le lien est déjà présent dans le registre ou si une limite a déjà été définie avec la `set_bound` fonction et qu’un lien a été supprimé depuis.

## <a name="begin"></a><a name="begin"></a> commencer

Retourne un itérateur au premier élément de l' `multi_link_registry` objet.

```cpp
virtual iterator begin();
```

### <a name="return-value"></a>Valeur renvoyée

Itérateur qui traite le premier élément de l' `multi_link_registry` objet.

### <a name="remarks"></a>Notes

L’état final est indiqué par un `NULL` lien.

## <a name="contains"></a><a name="contains"></a> comprend

Recherche `multi_link_registry` un bloc spécifié dans l’objet.

```cpp
virtual bool contains(_EType _Link);
```

### <a name="parameters"></a>Paramètres

*_Link*<br/>
Pointeur vers un bloc qui doit être recherché dans l' `multi_link_registry` objet.

### <a name="return-value"></a>Valeur renvoyée

**`true`** Si le bloc spécifié a été trouvé ; **`false`** sinon,.

## <a name="count"></a><a name="count"></a> saut

Compte le nombre d’éléments dans l' `multi_link_registry` objet.

```cpp
virtual size_t count();
```

### <a name="return-value"></a>Valeur renvoyée

Nombre d'éléments de l'objet `multi_link_registry`.

## <a name="multi_link_registry"></a><a name="ctor"></a> multi_link_registry

Construit un objet `multi_link_registry`.

```cpp
multi_link_registry();
```

## <a name="multi_link_registry"></a><a name="dtor"></a> ~ multi_link_registry

Détruit l' `multi_link_registry` objet.

```cpp
virtual ~multi_link_registry();
```

### <a name="remarks"></a>Notes

La méthode lève une exception [invalid_operation](invalid-operation-class.md) si elle est appelée avant la suppression de tous les liens.

## <a name="remove"></a><a name="remove"></a> Installez

Supprime un lien de l' `multi_link_registry` objet.

```cpp
virtual bool remove(_EType _Link);
```

### <a name="parameters"></a>Paramètres

*_Link*<br/>
Pointeur vers un bloc à supprimer, s’il est trouvé.

### <a name="return-value"></a>Valeur renvoyée

**`true`** Si le lien a été trouvé et supprimé ; **`false`** sinon,.

## <a name="set_bound"></a><a name="set_bound"></a> set_bound

Définit une limite supérieure du nombre de liens que l' `multi_link_registry` objet peut contenir.

```cpp
void set_bound(size_t _MaxLinks);
```

### <a name="parameters"></a>Paramètres

*_MaxLinks*<br/>
Nombre maximal de liens que l' `multi_link_registry` objet peut contenir.

### <a name="remarks"></a>Notes

Une fois qu’une limite est définie, la dissociation d’une entrée amène l' `multi_link_registry` objet à entrer dans un état immuable où d’autres appels à `add` lèvera une `invalid_link_target` exception.

## <a name="see-also"></a>Voir aussi

[Espace de noms d’accès concurrentiel](concurrency-namespace.md)<br/>
[Classe single_link_registry](single-link-registry-class.md)
