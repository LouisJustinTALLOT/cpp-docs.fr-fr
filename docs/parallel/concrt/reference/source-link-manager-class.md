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
ms.openlocfilehash: 98f99bb5aec85a640eaf83a07fae3a1b667f7d91
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228425"
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

|Nom|Description|
|----------|-----------------|
|`const_pointer`|Type qui fournit un pointeur vers un **`const`** élément d’un `source_link_manager` objet.|
|`const_reference`|Type qui fournit une référence à un **`const`** élément stocké dans un `source_link_manager` objet pour la lecture et l’exécution d’opérations const.|
|`iterator`|Type qui fournit un itérateur capable de lire ou de modifier tout élément de l' `source_link_manager` objet.|
|`type`|Type de registre de liens géré par l' `source_link_manager` objet.|

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[source_link_manager](#ctor)|Construit un objet `source_link_manager`.|
|[Destructeur ~ source_link_manager](#dtor)|Détruit l' `source_link_manager` objet.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[add](#add)|Ajoute un lien source à l' `source_link_manager` objet.|
|[commencer](#begin)|Retourne un itérateur au premier élément de l' `source_link_manager` objet.|
|[contains](#contains)|Recherche `network_link_registry` dans cet `source_link_manager` objet un bloc spécifié.|
|[count](#count)|Compte le nombre de blocs liés dans l' `source_link_manager` objet.|
|[reference](#reference)|Acquiert une référence sur l' `source_link_manager` objet.|
|[register_target_block](#register_target_block)|Inscrit le bloc cible qui contient cet `source_link_manager` objet.|
|[3/05](#release)|Libère la référence sur l' `source_link_manager` objet.|
|[remove](#remove)|Supprime un lien de l' `source_link_manager` objet.|
|[set_bound](#set_bound)|Définit le nombre maximal de liens source qui peuvent être ajoutés à cet `source_link_manager` objet.|

## <a name="remarks"></a>Notes

Actuellement, les blocs sources sont décomptés par référence. Il s’agit d’un wrapper sur un `network_link_registry` objet qui autorise l’accès simultané aux liens et fournit la possibilité de référencer les liens via des rappels. Les blocs de message ( `target_block` s ou `propagator_block` s) doivent utiliser cette classe pour leurs liens source.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`source_link_manager`

## <a name="requirements"></a>Spécifications

**En-tête :** agents.h

**Espace de noms :** concurrence

## <a name="add"></a><a name="add"></a>complémentaires

Ajoute un lien source à l' `source_link_manager` objet.

```cpp
void add(_EType _Link);
```

### <a name="parameters"></a>Paramètres

*_Link*<br/>
Pointeur vers un bloc à ajouter.

## <a name="begin"></a><a name="begin"></a>commencer

Retourne un itérateur au premier élément de l' `source_link_manager` objet.

```cpp
iterator begin();
```

### <a name="return-value"></a>Valeur de retour

Itérateur qui traite le premier élément de l' `source_link_manager` objet.

### <a name="remarks"></a>Notes

L’état final de l’itérateur est indiqué par un `NULL` lien.

## <a name="contains"></a><a name="contains"></a>comprend

Recherche `network_link_registry` dans cet `source_link_manager` objet un bloc spécifié.

```cpp
bool contains(_EType _Link);
```

### <a name="parameters"></a>Paramètres

*_Link*<br/>
Pointeur vers un bloc qui doit être recherché dans l' `source_link_manager` objet.

### <a name="return-value"></a>Valeur de retour

**`true`** Si le bloc spécifié a été trouvé ; **`false`** sinon,.

## <a name="count"></a><a name="count"></a>saut

Compte le nombre de blocs liés dans l' `source_link_manager` objet.

```cpp
size_t count();
```

### <a name="return-value"></a>Valeur de retour

Nombre de blocs liés dans l' `source_link_manager` objet.

## <a name="reference"></a><a name="reference"></a>faire

Acquiert une référence sur l' `source_link_manager` objet.

```cpp
void reference();
```

## <a name="register_target_block"></a><a name="register_target_block"></a>register_target_block

Inscrit le bloc cible qui contient cet `source_link_manager` objet.

```cpp
void register_target_block(_Inout_ ITarget<typename _Block::source_type>* _PTarget);
```

### <a name="parameters"></a>Paramètres

*_PTarget*<br/>
Bloc cible contenant cet `source_link_manager` objet.

## <a name="release"></a><a name="release"></a>3/05

Libère la référence sur l' `source_link_manager` objet.

```cpp
void release();
```

## <a name="remove"></a><a name="remove"></a>Installez

Supprime un lien de l' `source_link_manager` objet.

```cpp
bool remove(_EType _Link);
```

### <a name="parameters"></a>Paramètres

*_Link*<br/>
Pointeur vers un bloc à supprimer, s’il est trouvé.

### <a name="return-value"></a>Valeur de retour

**`true`** Si le lien a été trouvé et supprimé ; **`false`** sinon,.

## <a name="set_bound"></a><a name="set_bound"></a>set_bound

Définit le nombre maximal de liens source qui peuvent être ajoutés à cet `source_link_manager` objet.

```cpp
void set_bound(size_t _MaxLinks);
```

### <a name="parameters"></a>Paramètres

*_MaxLinks*<br/>
Nombre maximal de liens.

## <a name="source_link_manager"></a><a name="ctor"></a>source_link_manager

Construit un objet `source_link_manager`.

```cpp
source_link_manager();
```

## <a name="source_link_manager"></a><a name="dtor"></a>~ source_link_manager

Détruit l' `source_link_manager` objet.

```cpp
~source_link_manager();
```

## <a name="see-also"></a>Voir aussi

[Espace de noms d’accès concurrentiel](concurrency-namespace.md)<br/>
[Classe single_link_registry](single-link-registry-class.md)<br/>
[Classe multi_link_registry](multi-link-registry-class.md)
