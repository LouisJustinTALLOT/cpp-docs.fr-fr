---
description: 'En savoir plus sur : classe ComPtrRef'
title: ComPtrRef (classe)
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::Details::ComPtrRef
- client/Microsoft::WRL::Details::ComPtrRef::ComPtrRef
- client/Microsoft::WRL::Details::ComPtrRef::GetAddressOf
- client/Microsoft::WRL::Details::ComPtrRef::operator==
- client/Microsoft::WRL::Details::ComPtrRef::operator!=
- client/Microsoft::WRL::Details::ComPtrRef::operator InterfaceType**
- client/Microsoft::WRL::Details::ComPtrRef::operator*
- client/Microsoft::WRL::Details::ComPtrRef::operator T*
- client/Microsoft::WRL::Details::ComPtrRef::operator void**
- client/Microsoft::WRL::Details::ComPtrRef::ReleaseAndGetAddressOf
helpviewer_keywords:
- Microsoft::WRL::Details::ComPtrRef class
- Microsoft::WRL::Details::ComPtrRef::ComPtrRef, constructor
- Microsoft::WRL::Details::ComPtrRef::GetAddressOf method
- Microsoft::WRL::Details::ComPtrRef::operator== operator
- Microsoft::WRL::Details::ComPtrRef::operator!= operator
- Microsoft::WRL::Details::ComPtrRef::operator InterfaceType** operator
- Microsoft::WRL::Details::ComPtrRef::operator* operator
- Microsoft::WRL::Details::ComPtrRef::operator T* operator
- Microsoft::WRL::Details::ComPtrRef::operator void** operator
- Microsoft::WRL::Details::ComPtrRef::ReleaseAndGetAddressOf method
ms.assetid: d6bdfd20-e977-45b4-9ac1-1b8efbdb77de
ms.openlocfilehash: 42a0698c8eb393c84422b52ee112013b91fe39e6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97273148"
---
# <a name="comptrref-class"></a>ComPtrRef (classe)

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

## <a name="syntax"></a>Syntaxe

```cpp
template <typename T>
class ComPtrRef : public ComPtrRefBase<T>;
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Type [ComPtr \<T> ](comptr-class.md) ou type dérivé de celui-ci, pas simplement l’interface représentée par `ComPtr` .

## <a name="remarks"></a>Notes

Représente une référence à un objet de type `ComPtr<T>` .

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

Nom                               | Description
---------------------------------- | -------------------------------------------------------------------------------------------------------------
[ComPtrRef :: ComPtrRef](#comptrref) | Initialise une nouvelle instance de la `ComPtrRef` classe à partir du pointeur spécifié vers un autre `ComPtrRef` objet.

### <a name="public-methods"></a>M&#233;thodes publiques

Nom                                                         | Description
------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------
[ComPtrRef :: Getaddressof,](#getaddressof)                     | Récupère l’adresse d’un pointeur vers l’interface représentée par l’objet actuel `ComPtrRef` .
[ComPtrRef :: Releaseandgetaddressof,](#releaseandgetaddressof) | Supprime l’objet actuel `ComPtrRef` et retourne un pointeur vers l’interface qui a été représenté par l' `ComPtrRef` objet.

### <a name="public-operators"></a>Op&#233;rateurs publics

Nom                                                                     | Description
------------------------------------------------------------------------ | -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
[ComPtrRef :: Operator InterfaceType * *](#operator-interfacetype-star-star) | Supprime l’objet actuel `ComPtrRef` et retourne un pointeur vers l’interface qui a été représenté par l' `ComPtrRef` objet.
[ComPtrRef :: Operator T *](#operator-t-star)                               | Retourne la valeur du membre de données [PTR_](comptrrefbase-class.md#ptr) de l’objet ComPtrRef actuel.
[ComPtrRef :: Operator void * *](#operator-void-star-star)                   | Supprime l’objet actuel `ComPtrRef` , effectue un cast du pointeur vers l’interface représentée par l' `ComPtrRef` objet en tant que pointeur vers pointeur **`void`** , puis retourne le pointeur de cast.
[ComPtrRef :: Operator *](#operator-star)                                   | Récupère le pointeur vers l’interface représentée par l’objet actuel `ComPtrRef` .
[ComPtrRef :: Operator = =](#operator-equality)                              | Indique si deux objets `ComPtrRef` sont égaux.
[ComPtrRef :: Operator ! =](#operator-inequality)                            | Indique si deux objets `ComPtrRef` ne sont pas égaux.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`ComPtrRefBase`

`ComPtrRef`

## <a name="requirements"></a>Spécifications

**En-tête :** client.h

**Espace de noms :** Microsoft :: WRL ::D étails

## <a name="comptrrefcomptrref"></a><a name="comptrref"></a> ComPtrRef :: ComPtrRef

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

```cpp
ComPtrRef(
   _In_opt_ T* ptr
);
```

### <a name="parameters"></a>Paramètres

*ptr*<br/>
Valeur sous-jacente d’un autre `ComPtrRef` objet.

### <a name="remarks"></a>Notes

Initialise une nouvelle instance de la `ComPtrRef` classe à partir du pointeur spécifié vers un autre `ComPtrRef` objet.

## <a name="comptrrefgetaddressof"></a><a name="getaddressof"></a> ComPtrRef :: Getaddressof,

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

```cpp
InterfaceType* const * GetAddressOf() const;
```

### <a name="return-value"></a>Valeur renvoyée

Adresse d’un pointeur vers l’interface représentée par l' `ComPtrRef` objet actuel.

### <a name="remarks"></a>Notes

Récupère l’adresse d’un pointeur vers l’interface représentée par l’objet actuel `ComPtrRef` .

## <a name="comptrrefoperator"></a><a name="operator-equality"></a> ComPtrRef :: Operator = =

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

```cpp
bool operator==(
   const Details::ComPtrRef<ComPtr<T>>& a,
   const Details::ComPtrRef<ComPtr<U>>& b
);

bool operator==(
   const Details::ComPtrRef<ComPtr<T>>& a,
   decltype(__nullptr)
);

bool operator==(
   decltype(__nullptr),
   const Details::ComPtrRef<ComPtr<T>>& a
);

bool operator==(
   const Details::ComPtrRef<ComPtr<T>>& a,
   void* b
);

bool operator==(
   void* b,
   const Details::ComPtrRef<ComPtr<T>>& a
);
```

### <a name="parameters"></a>Paramètres

*un*<br/>
Référence à un objet `ComPtrRef`.

*b*<br/>
Une référence à un autre `ComPtrRef` objet ou un pointeur vers un type anonyme ( **`void*`** ).

### <a name="return-value"></a>Valeur renvoyée

Le premier opérateur produit **`true`** si l’objet *a* est égal à l’objet *b*; sinon, **`false`** .

Le deuxième et le troisième opérateur produisent **`true`** si l’objet *a* est égal à **`nullptr`** ; sinon, **`false`** .

Les quatrième et cinquième opérateurs produisent **`true`** si l’objet *a* est égal à l’objet *b*; sinon, **`false`** .

### <a name="remarks"></a>Notes

Indique si deux objets `ComPtrRef` sont égaux.

## <a name="comptrrefoperator"></a><a name="operator-inequality"></a> ComPtrRef :: Operator ! =

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

```cpp
bool operator!=(
   const Details::ComPtrRef<ComPtr<T>>& a,
   const Details::ComPtrRef<ComPtr<U>>& b
);

bool operator!=(
   const Details::ComPtrRef<ComPtr<T>>& a,
   decltype(__nullptr)
);

bool operator!=(
   decltype(__nullptr),
   const Details::ComPtrRef<ComPtr<T>>& a
);

bool operator!=(
   const Details::ComPtrRef<ComPtr<T>>& a,
   void* b
);

bool operator!=(
   void* b,
   const Details::ComPtrRef<ComPtr<T>>& a
);
```

### <a name="parameters"></a>Paramètres

*un*<br/>
Référence à un objet `ComPtrRef`.

*b*<br/>
Une référence à un autre `ComPtrRef` objet ou un pointeur vers un objet anonyme ( **`void*`** ).

### <a name="return-value"></a>Valeur renvoyée

Le premier opérateur produit **`true`** si l’objet *a* n’est pas égal à l’objet *b*; sinon, **`false`** .

Le deuxième et le troisième opérateur produisent **`true`** si l’objet *a* n’est pas égal à **`nullptr`** ; sinon, **`false`** .

Les quatrième et cinquième opérateurs produisent **`true`** si l’objet *a* n’est pas égal à l’objet *b*; sinon, **`false`** .

### <a name="remarks"></a>Notes

Indique si deux objets `ComPtrRef` ne sont pas égaux.

## <a name="comptrrefoperator-interfacetype"></a><a name="operator-interfacetype-star-star"></a> ComPtrRef :: Operator InterfaceType\*\*

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

```cpp
operator InterfaceType**();
```

### <a name="remarks"></a>Notes

Supprime l’objet actuel `ComPtrRef` et retourne un pointeur vers l’interface qui a été représenté par l' `ComPtrRef` objet.

## <a name="comptrrefoperator"></a><a name="operator-star"></a> ComPtrRef :: Operator *

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

```cpp
InterfaceType* operator *();
```

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers l’interface représentée par l' `ComPtrRef` objet actuel.

### <a name="remarks"></a>Notes

Récupère le pointeur vers l’interface représentée par l’objet actuel `ComPtrRef` .

## <a name="comptrrefoperator-t"></a><a name="operator-t-star"></a> ComPtrRef :: Operator T *

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

```cpp
operator T*();
```

### <a name="remarks"></a>Notes

Retourne la valeur du membre de données [PTR_](comptrrefbase-class.md#ptr) de l' `ComPtrRef` objet actuel.

## <a name="comptrrefoperator-void"></a><a name="operator-void-star-star"></a> ComPtrRef :: Operator void\*\*

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

```cpp
operator void**() const;
```

### <a name="remarks"></a>Notes

Supprime l’objet actuel `ComPtrRef` , effectue un cast du pointeur vers l’interface représentée par l' `ComPtrRef` objet en tant que pointeur vers pointeur **`void`** , puis retourne le pointeur de cast.

## <a name="comptrrefreleaseandgetaddressof"></a><a name="releaseandgetaddressof"></a> ComPtrRef :: Releaseandgetaddressof,

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

```cpp
InterfaceType** ReleaseAndGetAddressOf();
```

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers l’interface qui a été représentée par l' `ComPtrRef` objet supprimé.

### <a name="remarks"></a>Notes

Supprime l’objet actuel `ComPtrRef` et retourne un pointeur vers l’interface qui a été représenté par l' `ComPtrRef` objet.
