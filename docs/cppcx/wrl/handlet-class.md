---
description: 'En savoir plus sur : classe Handlet'
title: HandleT (classe)
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleT
- corewrappers/Microsoft::WRL::Wrappers::HandleT::Attach
- corewrappers/Microsoft::WRL::Wrappers::HandleT::Close
- corewrappers/Microsoft::WRL::Wrappers::HandleT::Detach
- corewrappers/Microsoft::WRL::Wrappers::HandleT::Get
- corewrappers/Microsoft::WRL::Wrappers::HandleT::handle_
- corewrappers/Microsoft::WRL::Wrappers::HandleT::HandleT
- corewrappers/Microsoft::WRL::Wrappers::HandleT::InternalClose
- corewrappers/Microsoft::WRL::Wrappers::HandleT::IsValid
- corewrappers/Microsoft::WRL::Wrappers::HandleT::operator=
- corewrappers/Microsoft::WRL::Wrappers::HandleT::~HandleT
helpviewer_keywords:
- Microsoft::WRL::Wrappers::HandleT class
- Microsoft::WRL::Wrappers::HandleT::Attach method
- Microsoft::WRL::Wrappers::HandleT::Close method
- Microsoft::WRL::Wrappers::HandleT::Detach method
- Microsoft::WRL::Wrappers::HandleT::Get method
- Microsoft::WRL::Wrappers::HandleT::handle_ data member
- Microsoft::WRL::Wrappers::HandleT::HandleT, constructor
- Microsoft::WRL::Wrappers::HandleT::InternalClose method
- Microsoft::WRL::Wrappers::HandleT::IsValid method
- Microsoft::WRL::Wrappers::HandleT::operator= operator
- Microsoft::WRL::Wrappers::HandleT::~HandleT, destructor
ms.assetid: 3822b32a-a426-4d94-a54d-919d4df60ee2
ms.openlocfilehash: 608433193729e3d9be5b9490c469bf0b04d3531c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97250008"
---
# <a name="handlet-class"></a>HandleT (classe)

Représente un handle vers un objet.

## <a name="syntax"></a>Syntaxe

```cpp
template <typename HandleTraits>
class HandleT;
```

### <a name="parameters"></a>Paramètres

*HandleTraits*<br/>
Instance de la structure [HandleTraits](handletraits-structure.md) qui définit les caractéristiques communes d’un handle.

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

Nom     | Description
-------- | -----------------------------
`Traits` | Synonyme de `HandleTraits`.

### <a name="public-constructors"></a>Constructeurs publics

Nom                                | Description
----------------------------------- | --------------------------------------------------
[Handlet :: Handlet](#handlet)        | Initialise une nouvelle instance de la classe `HandleT`.
[Handler :: ~ Handlet](#tilde-handlet) | Déinitialise une instance de la `HandleT` classe.

### <a name="public-methods"></a>M&#233;thodes publiques

Nom                         | Description
---------------------------- | ----------------------------------------------------------------------
[Handlet :: Attach](#attach)   | Associe le handle spécifié à l' `HandleT` objet actuel.
[Handlet :: Close](#close)     | Ferme l'objet `HandleT` en cours.
[Handlet ::D Etach](#detach)   | Dissocie l’objet actuel `HandleT` de son handle sous-jacent.
[Handlet :: obtient](#get)         | Obtient la valeur du handle sous-jacent.
[Handlet :: IsValid](#isvalid) | Indique si l' `HandleT` objet actuel représente un handle.

### <a name="protected-methods"></a>Méthodes protégées

Nom                                     | Description
---------------------------------------- | ------------------------------------
[Handlet :: Internalclose,](#internalclose) | Ferme l'objet `HandleT` en cours.

### <a name="public-operators"></a>Op&#233;rateurs publics

Nom                                   | Description
-------------------------------------- | ----------------------------------------------------------------------------------
[Handlet :: Operator =](#operator-assign) | Déplace la valeur de l' `HandleT` objet spécifié vers l' `HandleT` objet actuel.

### <a name="protected-data-members"></a>Membres de données protégés

Nom                        | Description
--------------------------- | ----------------------------------------------------------------
[Handlet :: handle_](#handle) | Contient le handle représenté par l' `HandleT` objet.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`HandleT`

## <a name="requirements"></a>Spécifications

**En-tête :** corewrappers. h

**Espace de noms :** Microsoft :: WRL :: wrappers

## <a name="handlethandlet"></a><a name="tilde-handlet"></a> Handler :: ~ Handlet

Déinitialise une instance de la `HandleT` classe.

```cpp
~HandleT();
```

## <a name="handletattach"></a><a name="attach"></a> Handlet :: Attach

Associe le handle spécifié à l' `HandleT` objet actuel.

```cpp
void Attach(
   typename HandleTraits::Type h
);
```

### <a name="parameters"></a>Paramètres

*h*<br/>
Handle.

## <a name="handletclose"></a><a name="close"></a> Handlet :: Close

Ferme l'objet `HandleT` en cours.

```cpp
void Close();
```

### <a name="remarks"></a>Notes

Le handle sous-jacent de l’objet actuel `HandleT` est fermé et le `HandleT` est défini sur l’état non valide.

Si le handle ne se ferme pas correctement, une exception est levée dans le thread appelant.

## <a name="handletdetach"></a><a name="detach"></a> Handlet ::D Etach

Dissocie l’objet actuel `HandleT` de son handle sous-jacent.

```cpp
typename HandleTraits::Type Detach();
```

### <a name="return-value"></a>Valeur renvoyée

Handle sous-jacent.

### <a name="remarks"></a>Notes

Lorsque cette opération est terminée, la `HandleT` valeur actuelle est définie sur l’état non valide.

## <a name="handletget"></a><a name="get"></a> Handlet :: obtient

Obtient la valeur du handle sous-jacent.

```cpp
typename HandleTraits::Type Get() const;
```

### <a name="return-value"></a>Valeur renvoyée

Handle.

## <a name="handlethandle_"></a><a name="handle"></a> Handlet :: handle_

Contient le handle représenté par l' `HandleT` objet.

```cpp
typename HandleTraits::Type handle_;
```

## <a name="handlethandlet"></a><a name="handlet"></a> Handlet :: Handlet

Initialise une nouvelle instance de la classe `HandleT`.

```cpp
explicit HandleT(
   typename HandleTraits::Type h =
      HandleTraits::GetInvalidValue()
);

HandleT(
   _Inout_ HandleT&& h
);
```

### <a name="parameters"></a>Paramètres

*h*<br/>
Handle.

### <a name="remarks"></a>Notes

Le premier constructeur initialise un `HandleT` objet qui n’est pas un handle valide à un objet. Le deuxième constructeur crée un nouvel `HandleT` objet à partir du paramètre *h*.

## <a name="handletinternalclose"></a><a name="internalclose"></a> Handlet :: Internalclose,

Ferme l'objet `HandleT` en cours.

```cpp
virtual bool InternalClose();
```

### <a name="return-value"></a>Valeur renvoyée

**`true`** Si le actuel s’est `HandleT` correctement fermé ; sinon, **`false`** .

### <a name="remarks"></a>Notes

`InternalClose()` est de **`protected`** .

## <a name="handletisvalid"></a><a name="isvalid"></a> Handlet :: IsValid

Indique si l' `HandleT` objet actuel représente un handle.

```cpp
bool IsValid() const;
```

### <a name="return-value"></a>Valeur renvoyée

**`true`** Si le `HandleT` représente un handle ; sinon, **`false`** .

## <a name="handletoperator"></a><a name="operator-assign"></a> Handlet :: Operator =

Déplace la valeur de l' `HandleT` objet spécifié vers l' `HandleT` objet actuel.

```cpp
HandleT& operator=(
   _Inout_ HandleT&& h
);
```

### <a name="parameters"></a>Paramètres

*h*<br/>
Référence rvalue à un handle.

### <a name="return-value"></a>Valeur renvoyée

Référence à l’objet actuel `HandleT` .

### <a name="remarks"></a>Notes

Cette opération invalide l' `HandleT` objet spécifié par le paramètre *h*.
