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
ms.openlocfilehash: 24f89a6b2fb998ba5e5a82dbb470accb45d0fd9f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219545"
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
Type de données de bloc stocké dans l' `single_link_registry` objet.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[single_link_registry](#ctor)|Construit un objet `single_link_registry`.|
|[Destructeur ~ single_link_registry](#dtor)|Détruit l' `single_link_registry` objet.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[add](#add)|Ajoute un lien à l' `single_link_registry` objet. (Substitue [network_link_registry :: Add](network-link-registry-class.md#add).)|
|[commencer](#begin)|Retourne un itérateur au premier élément de l' `single_link_registry` objet. (Substitue [network_link_registry :: Begin](network-link-registry-class.md#begin).)|
|[contains](#contains)|Recherche `single_link_registry` un bloc spécifié dans l’objet. (Substitue [network_link_registry :: Contains](network-link-registry-class.md#contains).)|
|[count](#count)|Compte le nombre d’éléments dans l' `single_link_registry` objet. (Substitue [network_link_registry :: Count](network-link-registry-class.md#count).)|
|[remove](#remove)|Supprime un lien de l' `single_link_registry` objet. (Substitue [network_link_registry :: Remove](network-link-registry-class.md#remove).)|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[network_link_registry](network-link-registry-class.md)

`single_link_registry`

## <a name="requirements"></a>Spécifications

**En-tête :** agents.h

**Espace de noms :** concurrence

## <a name="add"></a><a name="add"></a>complémentaires

Ajoute un lien à l' `single_link_registry` objet.

```cpp
virtual void add(_EType _Link);
```

### <a name="parameters"></a>Paramètres

*_Link*<br/>
Pointeur vers un bloc à ajouter.

### <a name="remarks"></a>Notes

La méthode lève une exception [invalid_link_target](invalid-link-target-class.md) s’il existe déjà un lien dans ce registre.

## <a name="begin"></a><a name="begin"></a>commencer

Retourne un itérateur au premier élément de l' `single_link_registry` objet.

```cpp
virtual iterator begin();
```

### <a name="return-value"></a>Valeur de retour

Itérateur qui traite le premier élément de l' `single_link_registry` objet.

### <a name="remarks"></a>Notes

L’état final est indiqué par un `NULL` lien.

## <a name="contains"></a><a name="contains"></a>comprend

Recherche `single_link_registry` un bloc spécifié dans l’objet.

```cpp
virtual bool contains(_EType _Link);
```

### <a name="parameters"></a>Paramètres

*_Link*<br/>
Pointeur vers un bloc qui doit être recherché dans l' `single_link_registry` objet.

### <a name="return-value"></a>Valeur de retour

**`true`** Si le lien a été trouvé ; **`false`** sinon,.

## <a name="count"></a><a name="count"></a>saut

Compte le nombre d’éléments dans l' `single_link_registry` objet.

```cpp
virtual size_t count();
```

### <a name="return-value"></a>Valeur de retour

Nombre d'éléments de l'objet `single_link_registry`.

## <a name="remove"></a><a name="remove"></a>Installez

Supprime un lien de l' `single_link_registry` objet.

```cpp
virtual bool remove(_EType _Link);
```

### <a name="parameters"></a>Paramètres

*_Link*<br/>
Pointeur vers un bloc à supprimer, s’il est trouvé.

### <a name="return-value"></a>Valeur de retour

**`true`** Si le lien a été trouvé et supprimé ; **`false`** sinon,.

## <a name="single_link_registry"></a><a name="ctor"></a>single_link_registry

Construit un objet `single_link_registry`.

```cpp
single_link_registry();
```

## <a name="single_link_registry"></a><a name="dtor"></a>~ single_link_registry

Détruit l' `single_link_registry` objet.

```cpp
virtual ~single_link_registry();
```

### <a name="remarks"></a>Notes

La méthode lève une exception [invalid_operation](invalid-operation-class.md) si elle est appelée avant la suppression du lien.

## <a name="see-also"></a>Voir aussi

[Espace de noms d’accès concurrentiel](concurrency-namespace.md)<br/>
[Classe multi_link_registry](multi-link-registry-class.md)
