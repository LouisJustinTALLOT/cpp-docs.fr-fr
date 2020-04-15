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
ms.openlocfilehash: bde7d7f1bd6730d96cb0f7a0d191a32eb8ed3e8c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371462"
---
# <a name="handlet-class"></a>HandleT (classe)

Représente une poignée à un objet.

## <a name="syntax"></a>Syntaxe

```cpp
template <typename HandleTraits>
class HandleT;
```

### <a name="parameters"></a>Paramètres

*PoignéeTraits*<br/>
Un exemple de la structure [HandleTraits](handletraits-structure.md) qui définit les caractéristiques communes d’une poignée.

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

Nom     | Description
-------- | -----------------------------
`Traits` | Synonyme de `HandleTraits`.

### <a name="public-constructors"></a>Constructeurs publics

Nom                                | Description
----------------------------------- | --------------------------------------------------
[Poignée::Handlet](#handlet)        | Initialise une nouvelle instance de la classe `HandleT`.
[Handlet: :-HandleT](#tilde-handlet) | Désinitialise un exemple `HandleT` de la classe.

### <a name="public-methods"></a>M&#233;thodes publiques

Nom                         | Description
---------------------------- | ----------------------------------------------------------------------
[HandleT::Attach](#attach)   | Associe la poignée spécifiée à l’objet actuel. `HandleT`
[HandleT::Fermer](#close)     | Ferme l'objet `HandleT` en cours.
[HandleT::Detach](#detach)   | Dissocie l’objet actuel `HandleT` de sa poignée sous-jacente.
[HandleT::Get](#get)         | Obtient la valeur de la poignée sous-jacente.
[Poignée::IsValid](#isvalid) | Indique si `HandleT` l’objet actuel représente une poignée.

### <a name="protected-methods"></a>Méthodes protégées

Nom                                     | Description
---------------------------------------- | ------------------------------------
[HandleT::InternalClose](#internalclose) | Ferme l'objet `HandleT` en cours.

### <a name="public-operators"></a>Op&#233;rateurs publics

Nom                                   | Description
-------------------------------------- | ----------------------------------------------------------------------------------
[HandleT::opérateur](#operator-assign) | Déplace la valeur `HandleT` de l’objet spécifié à l’objet actuel. `HandleT`

### <a name="protected-data-members"></a>Membres de données protégés

Nom                        | Description
--------------------------- | ----------------------------------------------------------------
[Poignée::handle_](#handle) | Contient la poignée qui est `HandleT` représentée par l’objet.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`HandleT`

## <a name="requirements"></a>Spécifications

**En-tête:** corewrappers.h

**Espace nom:** Microsoft::WRL::Wrappers

## <a name="handlethandlet"></a><a name="tilde-handlet"></a>Handlet: :-HandleT

Désinitialise un exemple `HandleT` de la classe.

```cpp
~HandleT();
```

## <a name="handletattach"></a><a name="attach"></a>HandleT::Attach

Associe la poignée spécifiée à l’objet actuel. `HandleT`

```cpp
void Attach(
   typename HandleTraits::Type h
);
```

### <a name="parameters"></a>Paramètres

*h*<br/>
Handle.

## <a name="handletclose"></a><a name="close"></a>HandleT::Fermer

Ferme l'objet `HandleT` en cours.

```cpp
void Close();
```

### <a name="remarks"></a>Notes

La poignée qui sous-tend le `HandleT` courant `HandleT` est fermée, et le est réglé à l’état invalide.

Si le manche ne se ferme pas correctement, une exception est soulevée dans le fil d’appel.

## <a name="handletdetach"></a><a name="detach"></a>HandleT::Detach

Dissocie l’objet actuel `HandleT` de sa poignée sous-jacente.

```cpp
typename HandleTraits::Type Detach();
```

### <a name="return-value"></a>Valeur de retour

La poignée sous-jacente.

### <a name="remarks"></a>Notes

Lorsque cette opération se `HandleT` termine, le courant est réglé à l’état invalide.

## <a name="handletget"></a><a name="get"></a>HandleT::Get

Obtient la valeur de la poignée sous-jacente.

```cpp
typename HandleTraits::Type Get() const;
```

### <a name="return-value"></a>Valeur de retour

Handle.

## <a name="handlethandle_"></a><a name="handle"></a>Poignée::handle_

Contient la poignée qui est `HandleT` représentée par l’objet.

```cpp
typename HandleTraits::Type handle_;
```

## <a name="handlethandlet"></a><a name="handlet"></a>Poignée::Handlet

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

Le premier constructeur initialise `HandleT` un objet qui n’est pas une poignée valide à un objet. Le deuxième constructeur crée `HandleT` un nouvel objet à partir du paramètre *h*.

## <a name="handletinternalclose"></a><a name="internalclose"></a>HandleT::InternalClose

Ferme l'objet `HandleT` en cours.

```cpp
virtual bool InternalClose();
```

### <a name="return-value"></a>Valeur de retour

**vrai** si `HandleT` le courant s’est refermé avec succès; autrement, **faux**.

### <a name="remarks"></a>Notes

`InternalClose()` a la valeur `protected`.

## <a name="handletisvalid"></a><a name="isvalid"></a>Poignée::IsValid

Indique si `HandleT` l’objet actuel représente une poignée.

```cpp
bool IsValid() const;
```

### <a name="return-value"></a>Valeur de retour

**vrai** si `HandleT` le représente une poignée; autrement, **faux**.

## <a name="handletoperator"></a><a name="operator-assign"></a>HandleT::opérateur

Déplace la valeur `HandleT` de l’objet spécifié à l’objet actuel. `HandleT`

```cpp
HandleT& operator=(
   _Inout_ HandleT&& h
);
```

### <a name="parameters"></a>Paramètres

*h*<br/>
Une référence rvalue à une poignée.

### <a name="return-value"></a>Valeur de retour

Une référence à `HandleT` l’objet actuel.

### <a name="remarks"></a>Notes

Cette opération invalide l’objet `HandleT` spécifié par le paramètre *h*.
