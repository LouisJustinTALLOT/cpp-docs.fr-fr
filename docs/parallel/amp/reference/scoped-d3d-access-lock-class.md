---
title: scoped_d3d_access_lock, classe
ms.date: 11/04/2016
f1_keywords:
- scoped_d3d_access_lock
- AMPRT/scoped_d3d_access_lock
- AMPRT/concurrency::direct3d::scoped_d3d_access_lock::scoped_d3d_access_lock
ms.assetid: 0ad333e6-9839-4736-a722-16d95d70c4b1
ms.openlocfilehash: b5a2d9dab9cba7b19fa0d0b1627f653f2c7fdc57
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77126394"
---
# <a name="scoped_d3d_access_lock-class"></a>scoped_d3d_access_lock, classe

Wrapper RAII pour un verrou d’accès D3D sur un objet accelerator_view.

## <a name="syntax"></a>Syntaxe

```cpp
class scoped_d3d_access_lock;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Name|Description|
|----------|-----------------|
|[Constructeur scoped_d3d_access_lock](#ctor)|Surchargé. Construit un objet `scoped_d3d_access_lock`. Le verrou est libéré lorsque cet objet est hors de portée.|
|[Destructeur ~ scoped_d3d_access_lock](#dtor)|Libère le verrou d’accès D3D sur l’objet `accelerator_view` associé.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Name|Description|
|----------|-----------------|
|[operator=](#operator_eq)|Prend possession d’un verrou d’un autre `scoped_d3d_access_lock`.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`scoped_d3d_access_lock`

## <a name="requirements"></a>Spécifications

**En-tête :** amprt. h

**Espace de noms :** Concurrency ::d irect3d

## <a name="ctor"></a>scoped_d3d_access_lock

Construit un objet `scoped_d3d_access_lock`. Le verrou est libéré lorsque cet objet est hors de portée.

```cpp
explicit scoped_d3d_access_lock(// [1] constructor
    accelerator_view& _Av);

explicit scoped_d3d_access_lock(// [2] constructor
    accelerator_view& _Av,
    adopt_d3d_access_lock_t _T);

scoped_d3d_access_lock(// [3] move constructor
    scoped_d3d_access_lock&& _Other);
```

### <a name="parameters"></a>Paramètres

*_Av*<br/>
`accelerator_view` pour le verrou à adopter.

*_T*<br/>
Objet `adopt_d3d_access_lock_t`.

*_Other*<br/>
Objet `scoped_d3d_access_lock` à partir duquel déplacer un verrou existant.

## <a name="construction"></a>Construction

[1] le constructeur acquiert un verrou d’accès D3D sur l’objet [accelerator_view](accelerator-view-class.md) donné. La construction se bloque jusqu’à ce que le verrou soit acquis.

le constructeur [2] adopte un verrou d’accès D3D à partir de l’objet [accelerator_view](accelerator-view-class.md) donné.

[3] le constructeur de déplacement prend un verrou d’accès D3D existant d’un autre objet `scoped_d3d_access_lock`. La construction n’est pas bloquée.

## <a name="dtor"></a>~ scoped_d3d_access_lock

Libère le verrou d’accès D3D sur l’objet `accelerator_view` associé.

```cpp
~scoped_d3d_access_lock();
```

## <a name="operator_eq"></a>opérateur =

Prend possession d’un verrou d’accès D3D à partir d’un autre objet `scoped_d3d_access_lock`, en libérant le verrou précédent.

```cpp
scoped_d3d_access_lock& operator= (scoped_d3d_access_lock&& _Other);
```

### <a name="parameters"></a>Paramètres

*_Other*<br/>
Accelerator_view à partir duquel déplacer le verrou d’accès D3D.

### <a name="return-value"></a>Valeur de retour

Référence à ce `scoped_accelerator_view_lock`.

## <a name="see-also"></a>Voir aussi

[Concurrency::direct3d, espace de noms](concurrency-direct3d-namespace.md)
