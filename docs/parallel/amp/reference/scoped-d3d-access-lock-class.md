---
title: Classe de scoped_d3d_access_lock | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: reference
f1_keywords:
- scoped_d3d_access_lock
- AMPRT/scoped_d3d_access_lock
- AMPRT/concurrency::direct3d::scoped_d3d_access_lock::scoped_d3d_access_lock
dev_langs:
- C++
ms.assetid: 0ad333e6-9839-4736-a722-16d95d70c4b1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b0bb3442de264e263ae0f0eabd93345eace1fde1
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50059608"
---
# <a name="scopedd3daccesslock-class"></a>scoped_d3d_access_lock, classe

Wrapper RAII pour un verrou d’accès D3D sur un objet accelerator_view.

### <a name="syntax"></a>Syntaxe

```
class scoped_d3d_access_lock;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[scoped_d3d_access_lock constructeur](#ctor)|Surchargé. Construit un objet `scoped_d3d_access_lock`. Le verrou est libéré lorsque cet objet est hors de portée.|
|[~ scoped_d3d_access_lock destructeur](#dtor)|Libère le verrou d’accès D3D sur associé `accelerator_view` objet.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[operator=](#operator_eq)|Prend possession d’un verrou d’un autre `scoped_d3d_access_lock`.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`scoped_d3d_access_lock`

## <a name="requirements"></a>Configuration requise

**En-tête :** amprt.h

**Namespace :** concurrency::direct3d

##  <a name="ctor"></a> scoped_d3d_access_lock

Construit un objet `scoped_d3d_access_lock`. Le verrou est libéré lorsque cet objet est hors de portée.

```
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
Le `accelerator_view` du verrou à adopter.

*_T*<br/>
Objet `adopt_d3d_access_lock_t`.

*_Autre*<br/>
Le `scoped_d3d_access_lock` objet à partir duquel déplacer un verrou existant.

## <a name="construction"></a>Construction

[1] constructeur acquiert un verrou d’accès D3D sur la donnée [accelerator_view](accelerator-view-class.md) objet. Blocs de construction jusqu'à ce que le verrou est acquis.

[2] constructeur adopter un verrou d’accès D3D à partir de la donnée [accelerator_view](accelerator-view-class.md) objet.

[3] constructeur de déplacement prend un verrou d’accès D3D existant d’un autre `scoped_d3d_access_lock` objet. Construction ne bloque pas.

##  <a name="dtor"></a> ~ scoped_d3d_access_lock

Libère le verrou d’accès D3D sur associé `accelerator_view` objet.

```
~scoped_d3d_access_lock();
```

## <a name="operator_eq"></a> opérateur =

Prend possession d’un verrou d’accès D3D à partir d’un autre `scoped_d3d_access_lock` objet, en libérant le verrou précédent.

```
scoped_d3d_access_lock& operator= (scoped_d3d_access_lock&& _Other);
```

### <a name="parameters"></a>Paramètres

*_Autre*<br/>
L’accelerator_view à partir duquel déplacer le verrou d’accès D3D.

### <a name="return-value"></a>Valeur de retour

Une référence à cet `scoped_accelerator_view_lock`.

## <a name="see-also"></a>Voir aussi

[Concurrency::direct3d, espace de noms](concurrency-direct3d-namespace.md)
