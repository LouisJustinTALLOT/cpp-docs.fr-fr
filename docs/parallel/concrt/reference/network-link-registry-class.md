---
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
ms.openlocfilehash: 430190c11ec06a4f26eb9d8c4237552848420ad7
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77138887"
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
Type de données de bloc stocké dans le `network_link_registry`.

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

|Name|Description|
|----------|-----------------|
|`const_pointer`|Type qui fournit un pointeur vers un élément `const` dans un objet `network_link_registry`.|
|`const_reference`|Type qui fournit une référence à un élément `const` stocké dans un objet `network_link_registry` pour la lecture et l’exécution d’opérations const.|
|`iterator`|Type qui fournit un itérateur capable de lire ou de modifier tout élément d’un objet `network_link_registry`.|
|`type`|Type qui représente le type de bloc stocké dans l’objet `network_link_registry`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Name|Description|
|----------|-----------------|
|[add](#add)|En cas de substitution dans une classe dérivée, ajoute un lien à l’objet `network_link_registry`.|
|[begin](#begin)|En cas de substitution dans une classe dérivée, retourne un itérateur au premier élément de l’objet `network_link_registry`.|
|[contains](#contains)|En cas de substitution dans une classe dérivée, recherche un bloc spécifié dans l’objet `network_link_registry`.|
|[count](#count)|En cas de substitution dans une classe dérivée, retourne le nombre d’éléments dans l’objet `network_link_registry`.|
|[remove](#remove)|En cas de substitution dans une classe dérivée, supprime un bloc spécifié de l’objet `network_link_registry`.|

## <a name="remarks"></a>Notes

La `network link registry` n’est pas sûre pour l’accès simultané.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`network_link_registry`

## <a name="requirements"></a>Spécifications

**En-tête :** agents.h

**Espace de noms :** concurrency

## <a name="add"></a>complémentaires

En cas de substitution dans une classe dérivée, ajoute un lien à l’objet `network_link_registry`.

```cpp
virtual void add(_EType _Link) = 0;
```

### <a name="parameters"></a>Paramètres

*_Link*<br/>
Pointeur vers un bloc à ajouter.

## <a name="begin"></a>commencer

En cas de substitution dans une classe dérivée, retourne un itérateur au premier élément de l’objet `network_link_registry`.

```cpp
virtual iterator begin() = 0;
```

### <a name="return-value"></a>Valeur de retour

Itérateur qui traite le premier élément de l’objet `network_link_registry`.

### <a name="remarks"></a>Notes

L’état final de l’itérateur est indiqué par un lien `NULL`.

## <a name="contains"></a>comprend

En cas de substitution dans une classe dérivée, recherche un bloc spécifié dans l’objet `network_link_registry`.

```cpp
virtual bool contains(_EType _Link) = 0;
```

### <a name="parameters"></a>Paramètres

*_Link*<br/>
Pointeur vers un bloc qui est recherché dans l’objet `network_link_registry`.

### <a name="return-value"></a>Valeur de retour

**true** si le bloc a été trouvé ; sinon, **false** .

## <a name="count"></a>saut

En cas de substitution dans une classe dérivée, retourne le nombre d’éléments dans l’objet `network_link_registry`.

```cpp
virtual size_t count() = 0;
```

### <a name="return-value"></a>Valeur de retour

Nombre d'éléments de l'objet `network_link_registry`.

## <a name="remove"></a>Installez

En cas de substitution dans une classe dérivée, supprime un bloc spécifié de l’objet `network_link_registry`.

```cpp
virtual bool remove(_EType _Link) = 0;
```

### <a name="parameters"></a>Paramètres

*_Link*<br/>
Pointeur vers un bloc à supprimer, s’il est trouvé.

### <a name="return-value"></a>Valeur de retour

**true** si le lien a été trouvé et supprimé ; sinon, **false** .

## <a name="see-also"></a>Voir aussi

[accès concurrentiel Namespace](concurrency-namespace.md)<br/>
[single_link_registry, classe](single-link-registry-class.md)<br/>
[multi_link_registry, classe](multi-link-registry-class.md)
