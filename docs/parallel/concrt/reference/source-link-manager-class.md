---
title: source_link_manager, classe
ms.date: 11/04/2016
f1_keywords:
- source_link_manager
- AGENTS/concurrency::source_link_manager
- AGENTS/concurrency::source_link_manager::source_link_manager
- AGENTS/concurrency::source_link_manager::add
- AGENTS/concurrency::source_link_manager::begin
- AGENTS/concurrency::source_link_manager::contains
- AGENTS/concurrency::source_link_manager::count
- AGENTS/concurrency::source_link_manager::reference
- AGENTS/concurrency::source_link_manager::register_target_block
- AGENTS/concurrency::source_link_manager::release
- AGENTS/concurrency::source_link_manager::remove
- AGENTS/concurrency::source_link_manager::set_bound
helpviewer_keywords:
- source_link_manager class
ms.assetid: 287487cf-e0fe-4c35-aa3c-24f081d1ddae
ms.openlocfilehash: 35c7cc72520cdb0675abf9c15574a49e33741d0b
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142695"
---
# <a name="source_link_manager-class"></a>source_link_manager, classe

L'objet `source_link_manager` gère les liens réseau des blocs de messagerie avec les blocs `ISource`.

## <a name="syntax"></a>Syntaxe

```cpp
template<class _LinkRegistry>
class source_link_manager;
```

### <a name="parameters"></a>Paramètres

*_LinkRegistry*<br/>
Registre de liens réseau.

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

|Name|Description|
|----------|-----------------|
|`const_pointer`|Type qui fournit un pointeur vers un élément `const` dans un objet `source_link_manager`.|
|`const_reference`|Type qui fournit une référence à un élément `const` stocké dans un objet `source_link_manager` pour la lecture et l’exécution d’opérations const.|
|`iterator`|Type qui fournit un itérateur capable de lire ou de modifier tout élément de l’objet `source_link_manager`.|
|`type`|Type de registre de liens géré par l’objet `source_link_manager`.|

### <a name="public-constructors"></a>Constructeurs publics

|Name|Description|
|----------|-----------------|
|[source_link_manager](#ctor)|Construit un objet `source_link_manager`.|
|[Destructeur ~ source_link_manager](#dtor)|Détruit l’objet `source_link_manager`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Name|Description|
|----------|-----------------|
|[add](#add)|Ajoute un lien source à l’objet `source_link_manager`.|
|[begin](#begin)|Retourne un itérateur au premier élément de l’objet `source_link_manager`.|
|[contains](#contains)|Recherche le `network_link_registry` dans cet objet `source_link_manager` pour un bloc spécifié.|
|[count](#count)|Compte le nombre de blocs liés dans l’objet `source_link_manager`.|
|[reference](#reference)|Acquiert une référence sur l’objet `source_link_manager`.|
|[register_target_block](#register_target_block)|Inscrit le bloc cible qui contient cet objet `source_link_manager`.|
|[release](#release)|Libère la référence sur l’objet `source_link_manager`.|
|[remove](#remove)|Supprime un lien de l’objet `source_link_manager`.|
|[set_bound](#set_bound)|Définit le nombre maximal de liens source qui peuvent être ajoutés à cet objet `source_link_manager`.|

## <a name="remarks"></a>Notes

Actuellement, les blocs sources sont décomptés par référence. Il s’agit d’un wrapper sur un objet `network_link_registry` qui autorise l’accès simultané aux liens et fournit la possibilité de référencer les liens via des rappels. Les blocs de messages (`target_block`s ou `propagator_block`s) doivent utiliser cette classe pour leurs liens source.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`source_link_manager`

## <a name="requirements"></a>Spécifications

**En-tête :** agents.h

**Espace de noms :** concurrency

## <a name="add"></a>complémentaires

Ajoute un lien source à l’objet `source_link_manager`.

```cpp
void add(_EType _Link);
```

### <a name="parameters"></a>Paramètres

*_Link*<br/>
Pointeur vers un bloc à ajouter.

## <a name="begin"></a>commencer

Retourne un itérateur au premier élément de l’objet `source_link_manager`.

```cpp
iterator begin();
```

### <a name="return-value"></a>Valeur de retour

Itérateur qui traite le premier élément de l’objet `source_link_manager`.

### <a name="remarks"></a>Notes

L’état final de l’itérateur est indiqué par un lien `NULL`.

## <a name="contains"></a>comprend

Recherche le `network_link_registry` dans cet objet `source_link_manager` pour un bloc spécifié.

```cpp
bool contains(_EType _Link);
```

### <a name="parameters"></a>Paramètres

*_Link*<br/>
Pointeur vers un bloc qui doit être recherché dans l’objet `source_link_manager`.

### <a name="return-value"></a>Valeur de retour

**true** si le bloc spécifié a été trouvé ; sinon, **false** .

## <a name="count"></a>saut

Compte le nombre de blocs liés dans l’objet `source_link_manager`.

```cpp
size_t count();
```

### <a name="return-value"></a>Valeur de retour

Nombre de blocs liés dans l’objet `source_link_manager`.

## <a name="reference"></a>faire

Acquiert une référence sur l’objet `source_link_manager`.

```cpp
void reference();
```

## <a name="register_target_block"></a>register_target_block

Inscrit le bloc cible qui contient cet objet `source_link_manager`.

```cpp
void register_target_block(_Inout_ ITarget<typename _Block::source_type>* _PTarget);
```

### <a name="parameters"></a>Paramètres

*_PTarget*<br/>
Bloc cible contenant cet objet `source_link_manager`.

## <a name="release"></a>3/05

Libère la référence sur l’objet `source_link_manager`.

```cpp
void release();
```

## <a name="remove"></a>Installez

Supprime un lien de l’objet `source_link_manager`.

```cpp
bool remove(_EType _Link);
```

### <a name="parameters"></a>Paramètres

*_Link*<br/>
Pointeur vers un bloc à supprimer, s’il est trouvé.

### <a name="return-value"></a>Valeur de retour

**true** si le lien a été trouvé et supprimé ; sinon, **false** .

## <a name="set_bound"></a>set_bound

Définit le nombre maximal de liens source qui peuvent être ajoutés à cet objet `source_link_manager`.

```cpp
void set_bound(size_t _MaxLinks);
```

### <a name="parameters"></a>Paramètres

*_MaxLinks*<br/>
Nombre maximal de liens.

## <a name="ctor"></a>source_link_manager

Construit un objet `source_link_manager`.

```cpp
source_link_manager();
```

## <a name="dtor"></a>~ source_link_manager

Détruit l’objet `source_link_manager`.

```cpp
~source_link_manager();
```

## <a name="see-also"></a>Voir aussi

[accès concurrentiel Namespace](concurrency-namespace.md)<br/>
[single_link_registry, classe](single-link-registry-class.md)<br/>
[multi_link_registry, classe](multi-link-registry-class.md)
