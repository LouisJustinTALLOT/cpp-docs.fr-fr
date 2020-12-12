---
description: 'En savoir plus sur : classe network_link_registry'
title: network_link_registry, classe
ms.date: 11/04/2016
f1_keywords:
- network_link_registry
- AGENTS/concurrency::network_link_registry
- AGENTS/concurrency::network_link_registry::add
- AGENTS/concurrency::network_link_registry::begin
- AGENTS/concurrency::network_link_registry::contains
- AGENTS/concurrency::network_link_registry::count
- AGENTS/concurrency::network_link_registry::remove
helpviewer_keywords:
- network_link_registry class
ms.assetid: 3e7b4097-09f1-4252-964e-b15b8f7f7fc6
ms.openlocfilehash: d14ec5758b399d46d5a5f04200b9422b030305f8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97236592"
---
# <a name="network_link_registry-class"></a>network_link_registry, classe

La classe de base abstraite `network_link_registry` gère les liens entre les blocs sources et cibles.

## <a name="syntax"></a>Syntaxe

```cpp
template<class _Block>
class network_link_registry;
```

### <a name="parameters"></a>Paramètres

*_Block*<br/>
Type de données de bloc stocké dans le `network_link_registry` .

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

|Nom|Description|
|----------|-----------------|
|`const_pointer`|Type qui fournit un pointeur vers un **`const`** élément d’un `network_link_registry` objet.|
|`const_reference`|Type qui fournit une référence à un **`const`** élément stocké dans un `network_link_registry` objet pour la lecture et l’exécution d’opérations const.|
|`iterator`|Type qui fournit un itérateur capable de lire ou de modifier tout élément d’un `network_link_registry` objet.|
|`type`|Type qui représente le type de bloc stocké dans l' `network_link_registry` objet.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[add](#add)|En cas de substitution dans une classe dérivée, ajoute un lien à l' `network_link_registry` objet.|
|[commencer](#begin)|En cas de substitution dans une classe dérivée, retourne un itérateur au premier élément de l' `network_link_registry` objet.|
|[contains](#contains)|En cas de substitution dans une classe dérivée, recherche `network_link_registry` un bloc spécifié dans l’objet.|
|[count](#count)|En cas de substitution dans une classe dérivée, retourne le nombre d’éléments dans l' `network_link_registry` objet.|
|[remove](#remove)|En cas de substitution dans une classe dérivée, supprime un bloc spécifié de l' `network_link_registry` objet.|

## <a name="remarks"></a>Notes

Le `network link registry` n’est pas sûr pour l’accès simultané.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`network_link_registry`

## <a name="requirements"></a>Spécifications

**En-tête :** agents.h

**Espace de noms :** concurrence

## <a name="add"></a><a name="add"></a> complémentaires

En cas de substitution dans une classe dérivée, ajoute un lien à l' `network_link_registry` objet.

```cpp
virtual void add(_EType _Link) = 0;
```

### <a name="parameters"></a>Paramètres

*_Link*<br/>
Pointeur vers un bloc à ajouter.

## <a name="begin"></a><a name="begin"></a> commencer

En cas de substitution dans une classe dérivée, retourne un itérateur au premier élément de l' `network_link_registry` objet.

```cpp
virtual iterator begin() = 0;
```

### <a name="return-value"></a>Valeur renvoyée

Itérateur qui traite le premier élément de l' `network_link_registry` objet.

### <a name="remarks"></a>Notes

L’état final de l’itérateur est indiqué par un `NULL` lien.

## <a name="contains"></a><a name="contains"></a> comprend

En cas de substitution dans une classe dérivée, recherche `network_link_registry` un bloc spécifié dans l’objet.

```cpp
virtual bool contains(_EType _Link) = 0;
```

### <a name="parameters"></a>Paramètres

*_Link*<br/>
Pointeur vers un bloc qui est recherché dans l' `network_link_registry` objet.

### <a name="return-value"></a>Valeur renvoyée

**`true`** Si le bloc a été trouvé ; **`false`** sinon,.

## <a name="count"></a><a name="count"></a> saut

En cas de substitution dans une classe dérivée, retourne le nombre d’éléments dans l' `network_link_registry` objet.

```cpp
virtual size_t count() = 0;
```

### <a name="return-value"></a>Valeur renvoyée

Nombre d'éléments de l'objet `network_link_registry`.

## <a name="remove"></a><a name="remove"></a> Installez

En cas de substitution dans une classe dérivée, supprime un bloc spécifié de l' `network_link_registry` objet.

```cpp
virtual bool remove(_EType _Link) = 0;
```

### <a name="parameters"></a>Paramètres

*_Link*<br/>
Pointeur vers un bloc à supprimer, s’il est trouvé.

### <a name="return-value"></a>Valeur renvoyée

**`true`** Si le lien a été trouvé et supprimé ; **`false`** sinon,.

## <a name="see-also"></a>Voir aussi

[Espace de noms d’accès concurrentiel](concurrency-namespace.md)<br/>
[Classe single_link_registry](single-link-registry-class.md)<br/>
[Classe multi_link_registry](multi-link-registry-class.md)
