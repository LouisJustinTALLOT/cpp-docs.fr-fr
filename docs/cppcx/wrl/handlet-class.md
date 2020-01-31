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
ms.openlocfilehash: f66fbe23c305be15e09928242175dfa7ce8c141b
ms.sourcegitcommit: b8c22e6d555cf833510753cba7a368d57e5886db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76821816"
---
# <a name="handlet-class"></a>HandleT (classe)

Représente un handle vers un objet.

## <a name="syntax"></a>Syntaxe

```cpp
template <typename HandleTraits>
class HandleT;
```

### <a name="parameters"></a>Parameters

*HandleTraits*<br/>
Instance de la structure [HandleTraits](handletraits-structure.md) qui définit les caractéristiques communes d’un handle.

## <a name="members"></a>Members

### <a name="public-typedefs"></a>Typedefs publics

Name     | Description
-------- | -----------------------------
`Traits` | Synonyme de `HandleTraits`.

### <a name="public-constructors"></a>Constructeurs publics

Name                                | Description
----------------------------------- | --------------------------------------------------
[HandleT::HandleT](#handlet)        | Initialise une nouvelle instance de la classe `HandleT` .
[Handler :: ~ Handlet](#tilde-handlet) | Déinitialise une instance de la classe `HandleT`.

### <a name="public-methods"></a>Méthodes publiques

Name                         | Description
---------------------------- | ----------------------------------------------------------------------
[HandleT::Attach](#attach)   | Associe le handle spécifié à l’objet `HandleT` actuel.
[HandleT::Close](#close)     | Ferme l’objet de `HandleT` actif.
[HandleT::Detach](#detach)   | Dissocie l’objet `HandleT` actuel de son handle sous-jacent.
[Handlet :: obtient](#get)         | Obtient la valeur du handle sous-jacent.
[Handlet :: IsValid](#isvalid) | Indique si l’objet `HandleT` actuel représente un handle.

### <a name="protected-methods"></a>Méthodes protégées

Name                                     | Description
---------------------------------------- | ------------------------------------
[Handlet :: Internalclose,](#internalclose) | Ferme l’objet de `HandleT` actif.

### <a name="public-operators"></a>Op&#233;rateurs publics

Name                                   | Description
-------------------------------------- | ----------------------------------------------------------------------------------
[HandleT::operator=](#operator-assign) | Déplace la valeur de l’objet `HandleT` spécifié vers l’objet `HandleT` actuel.

### <a name="protected-data-members"></a>Membres de données protégées

Name                        | Description
--------------------------- | ----------------------------------------------------------------
[Handlet :: handle_](#handle) | Contient le handle représenté par l’objet `HandleT`.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`HandleT`

## <a name="requirements"></a>Configuration requise pour

**En-tête :** corewrappers. h

**Espace de noms :** Microsoft :: WRL :: wrappers

## <a name="tilde-handlet"></a>Handler :: ~ Handlet

Déinitialise une instance de la classe `HandleT`.

```cpp
~HandleT();
```

## <a name="attach"></a>HandleT::Attach

Associe le handle spécifié à l’objet `HandleT` actuel.

```cpp
void Attach(
   typename HandleTraits::Type h
);
```

### <a name="parameters"></a>Parameters

*h*<br/>
Handle.

## <a name="close"></a>HandleT::Close

Ferme l’objet de `HandleT` actif.

```cpp
void Close();
```

### <a name="remarks"></a>Notes

Le handle sous-jacent du `HandleT` actuel est fermé et le `HandleT` est défini sur l’état non valide.

Si le handle ne se ferme pas correctement, une exception est levée dans le thread appelant.

## <a name="detach"></a>HandleT::Detach

Dissocie l’objet `HandleT` actuel de son handle sous-jacent.

```cpp
typename HandleTraits::Type Detach();
```

### <a name="return-value"></a>Valeur de retour

Handle sous-jacent.

### <a name="remarks"></a>Notes

Lorsque cette opération est terminée, le `HandleT` actuel est défini sur l’état non valide.

## <a name="get"></a>Handlet :: obtient

Obtient la valeur du handle sous-jacent.

```cpp
typename HandleTraits::Type Get() const;
```

### <a name="return-value"></a>Valeur de retour

Handle.

## <a name="handle"></a>HandleT::handle_

Contient le handle représenté par l’objet `HandleT`.

```cpp
typename HandleTraits::Type handle_;
```

## <a name="handlet"></a>HandleT::HandleT

Initialise une nouvelle instance de la classe `HandleT` .

```cpp
explicit HandleT(
   typename HandleTraits::Type h =
      HandleTraits::GetInvalidValue()
);

HandleT(
   _Inout_ HandleT&& h
);
```

### <a name="parameters"></a>Parameters

*h*<br/>
Handle.

### <a name="remarks"></a>Notes

Le premier constructeur initialise un objet `HandleT` qui n’est pas un handle valide d’un objet. Le deuxième constructeur crée un nouvel objet `HandleT` à partir du paramètre *h*.

## <a name="internalclose"></a>Handlet :: Internalclose,

Ferme l’objet de `HandleT` actif.

```cpp
virtual bool InternalClose();
```

### <a name="return-value"></a>Valeur de retour

**true** si l' `HandleT` actuel s’est correctement fermée ; Sinon, **false**.

### <a name="remarks"></a>Notes

`InternalClose()` est `protected`.

## <a name="isvalid"></a>Handlet :: IsValid

Indique si l’objet `HandleT` actuel représente un handle.

```cpp
bool IsValid() const;
```

### <a name="return-value"></a>Valeur de retour

**true** si le `HandleT` représente un handle ; Sinon, **false**.

## <a name="operator-assign"></a>HandleT::operator=

Déplace la valeur de l’objet `HandleT` spécifié vers l’objet `HandleT` actuel.

```cpp
HandleT& operator=(
   _Inout_ HandleT&& h
);
```

### <a name="parameters"></a>Parameters

*h*<br/>
Référence rvalue à un handle.

### <a name="return-value"></a>Valeur de retour

Référence à l’objet de `HandleT` actuel.

### <a name="remarks"></a>Notes

Cette opération invalide l’objet `HandleT` spécifié par le paramètre *h*.
