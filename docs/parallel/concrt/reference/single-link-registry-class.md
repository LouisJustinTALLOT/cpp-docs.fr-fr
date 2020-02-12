---
title: single_link_registry, classe
ms.date: 11/04/2016
f1_keywords:
- single_link_registry
- AGENTS/concurrency::single_link_registry
- AGENTS/concurrency::single_link_registry::single_link_registry
- AGENTS/concurrency::single_link_registry::add
- AGENTS/concurrency::single_link_registry::begin
- AGENTS/concurrency::single_link_registry::contains
- AGENTS/concurrency::single_link_registry::count
- AGENTS/concurrency::single_link_registry::remove
helpviewer_keywords:
- single_link_registry class
ms.assetid: 09540a4e-c34e-4ff9-af49-21b8612b6ab3
ms.openlocfilehash: c29caf6d31df316e80b15fe6827c81e34ece8a18
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142723"
---
# <a name="single_link_registry-class"></a>single_link_registry, classe

L'objet `single_link_registry` est un `network_link_registry` qui gère uniquement un seul bloc source ou cible.

## <a name="syntax"></a>Syntaxe

```cpp
template<class _Block>
class single_link_registry : public network_link_registry<_Block>;
```

### <a name="parameters"></a>Paramètres

*_Block*<br/>
Type de données de bloc stocké dans l’objet `single_link_registry`.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Name|Description|
|----------|-----------------|
|[single_link_registry](#ctor)|Construit un objet `single_link_registry`.|
|[Destructeur ~ single_link_registry](#dtor)|Détruit l’objet `single_link_registry`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Name|Description|
|----------|-----------------|
|[add](#add)|Ajoute un lien à l’objet `single_link_registry`. (Substitue [network_link_registry :: Add](network-link-registry-class.md#add).)|
|[begin](#begin)|Retourne un itérateur au premier élément de l’objet `single_link_registry`. (Substitue [network_link_registry :: Begin](network-link-registry-class.md#begin).)|
|[contains](#contains)|Recherche un bloc spécifié dans l’objet `single_link_registry`. (Substitue [network_link_registry :: Contains](network-link-registry-class.md#contains).)|
|[count](#count)|Compte le nombre d’éléments dans l’objet `single_link_registry`. (Substitue [network_link_registry :: Count](network-link-registry-class.md#count).)|
|[remove](#remove)|Supprime un lien de l’objet `single_link_registry`. (Substitue [network_link_registry :: Remove](network-link-registry-class.md#remove).)|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[network_link_registry](network-link-registry-class.md)

`single_link_registry`

## <a name="requirements"></a>Spécifications

**En-tête :** agents.h

**Espace de noms :** concurrency

## <a name="add"></a>complémentaires

Ajoute un lien à l’objet `single_link_registry`.

```cpp
virtual void add(_EType _Link);
```

### <a name="parameters"></a>Paramètres

*_Link*<br/>
Pointeur vers un bloc à ajouter.

### <a name="remarks"></a>Notes

La méthode lève une exception [invalid_link_target](invalid-link-target-class.md) s’il existe déjà un lien dans ce registre.

## <a name="begin"></a>commencer

Retourne un itérateur au premier élément de l’objet `single_link_registry`.

```cpp
virtual iterator begin();
```

### <a name="return-value"></a>Valeur de retour

Itérateur qui traite le premier élément de l’objet `single_link_registry`.

### <a name="remarks"></a>Notes

L’état final est indiqué par un lien `NULL`.

## <a name="contains"></a>comprend

Recherche un bloc spécifié dans l’objet `single_link_registry`.

```cpp
virtual bool contains(_EType _Link);
```

### <a name="parameters"></a>Paramètres

*_Link*<br/>
Pointeur vers un bloc qui doit être recherché dans l’objet `single_link_registry`.

### <a name="return-value"></a>Valeur de retour

**true** si le lien a été trouvé ; sinon, **false** .

## <a name="count"></a>saut

Compte le nombre d’éléments dans l’objet `single_link_registry`.

```cpp
virtual size_t count();
```

### <a name="return-value"></a>Valeur de retour

Nombre d'éléments de l'objet `single_link_registry`.

## <a name="remove"></a>Installez

Supprime un lien de l’objet `single_link_registry`.

```cpp
virtual bool remove(_EType _Link);
```

### <a name="parameters"></a>Paramètres

*_Link*<br/>
Pointeur vers un bloc à supprimer, s’il est trouvé.

### <a name="return-value"></a>Valeur de retour

**true** si le lien a été trouvé et supprimé ; sinon, **false** .

## <a name="ctor"></a>single_link_registry

Construit un objet `single_link_registry`.

```cpp
single_link_registry();
```

## <a name="dtor"></a>~ single_link_registry

Détruit l’objet `single_link_registry`.

```cpp
virtual ~single_link_registry();
```

### <a name="remarks"></a>Notes

La méthode lève une exception [invalid_operation](invalid-operation-class.md) si elle est appelée avant la suppression du lien.

## <a name="see-also"></a>Voir aussi

[accès concurrentiel Namespace](concurrency-namespace.md)<br/>
[multi_link_registry, classe](multi-link-registry-class.md)
