---
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
ms.openlocfilehash: 6e5824da03fb85e52f413f5678ea6e0fd6c77ddd
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/01/2019
ms.locfileid: "58784691"
---
# <a name="handlet-class"></a>HandleT (classe)

Représente un handle à un objet.

## <a name="syntax"></a>Syntaxe

```cpp
template <typename HandleTraits>
class HandleT;
```

### <a name="parameters"></a>Paramètres

*HandleTraits*<br/>
Une instance de la [HandleTraits](handletraits-structure.md) structure qui définit les caractéristiques communes d’une poignée.

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

Nom     | Description
-------- | -----------------------------
`Traits` | Synonyme de `HandleTraits`.

### <a name="public-constructors"></a>Constructeurs publics

Nom                                | Description
----------------------------------- | --------------------------------------------------
[HandleT::HandleT](#handlet)        | Initialise une nouvelle instance de la classe `HandleT`.
[HandleT::~HandleT](#tilde-handlet) | Annule l’initialisation d’une instance de la `HandleT` classe.

### <a name="public-methods"></a>M&#233;thodes publiques

Nom                         | Description
---------------------------- | ----------------------------------------------------------------------
[HandleT::Attach](#attach)   | Associe le handle spécifié actuel `HandleT` objet.
[HandleT::Close](#close)     | Ferme actuel `HandleT` objet.
[HandleT::Detach](#detach)   | Dissocie actuel `HandleT` objet à partir de son handle sous-jacent.
[HandleT::Get](#get)         | Obtient la valeur du handle sous-jacent.
[HandleT::IsValid](#isvalid) | Indique si l’actuel `HandleT` objet représente un handle.

### <a name="protected-methods"></a>Méthodes protégées

Nom                                     | Description
---------------------------------------- | ------------------------------------
[HandleT::InternalClose](#internalclose) | Ferme actuel `HandleT` objet.

### <a name="public-operators"></a>Op&#233;rateurs publics

Nom                                   | Description
-------------------------------------- | ----------------------------------------------------------------------------------
[HandleT::operator=](#operator-assign) | Déplace la valeur de l’objet `HandleT` objet actuel `HandleT` objet.

### <a name="protected-data-members"></a>Membres de données protégés

Nom                        | Description
--------------------------- | ----------------------------------------------------------------
[HandleT::handle_](#handle) | Contient le handle qui est représenté par le `HandleT` objet.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`HandleT`

## <a name="requirements"></a>Configuration requise

**En-tête :** corewrappers.h

**Espace de noms :** Microsoft::wrl::wrappers

## <a name="tilde-handlet"></a>HandleT::~HandleT

Annule l’initialisation d’une instance de la `HandleT` classe.

```cpp
~HandleT();
```

## <a name="attach"></a>HandleT::Attach

Associe le handle spécifié actuel `HandleT` objet.

```cpp
void Attach(
   typename HandleTraits::Type h
);
```

### <a name="parameters"></a>Paramètres

*h*<br/>
Un handle.

## <a name="close"></a>HandleT::Close

Ferme actuel `HandleT` objet.

```cpp
void Close();
```

### <a name="remarks"></a>Notes

Le handle sous-jacent actuel `HandleT` est fermée et le `HandleT` est défini sur l’état non valide.

Si le handle ne ferme pas correctement, une exception est levée dans le thread appelant.

## <a name="detach"></a>HandleT::Detach

Dissocie actuel `HandleT` objet à partir de son handle sous-jacent.

```cpp
typename HandleTraits::Type Detach();
```

### <a name="return-value"></a>Valeur de retour

Le handle sous-jacent.

### <a name="remarks"></a>Notes

Lorsque cette opération se termine, actuel `HandleT` est défini sur l’état non valide.

## <a name="get"></a>HandleT::Get

Obtient la valeur du handle sous-jacent.

```cpp
typename HandleTraits::Type Get() const;
```

### <a name="return-value"></a>Valeur de retour

Un handle.

## <a name="handle"></a>HandleT::handle_

Contient le handle qui est représenté par le `HandleT` objet.

```cpp
typename HandleTraits::Type handle_;
```

## <a name="handlet"></a>HandleT::HandleT

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
Un handle.

### <a name="remarks"></a>Notes

Le premier constructeur initialise un `HandleT` objet qui n’est pas un handle valide à un objet. Le deuxième constructeur crée un nouveau `HandleT` objet de paramètre *h*.

## <a name="internalclose"></a>HandleT::InternalClose

Ferme actuel `HandleT` objet.

```cpp
virtual bool InternalClose();
```

### <a name="return-value"></a>Valeur de retour

**true** si actuel `HandleT` fermé avec succès ; sinon, **false**.

### <a name="remarks"></a>Notes

`InternalClose()` a la valeur `protected`.

## <a name="isvalid"></a>HandleT::IsValid

Indique si l’actuel `HandleT` objet représente un handle.

```cpp
bool IsValid() const;
```

### <a name="return-value"></a>Valeur de retour

**true** si le `HandleT` représente un handle ; sinon, **false**.

## <a name="operator-assign"></a>HandleT::operator=

Déplace la valeur de l’objet `HandleT` objet actuel `HandleT` objet.

```cpp
HandleT& operator=(
   _Inout_ HandleT&& h
);
```

### <a name="parameters"></a>Paramètres

*h*<br/>
Une référence rvalue à un handle.

### <a name="return-value"></a>Valeur de retour

Une référence à l’actuel `HandleT` objet.

### <a name="remarks"></a>Notes

Cette opération invalide le `HandleT` objet spécifié par le paramètre *h*.
