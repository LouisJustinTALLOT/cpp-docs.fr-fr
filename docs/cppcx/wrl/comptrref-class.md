---
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
ms.openlocfilehash: df9ded817227547493c04035e0abc3d948e24495
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372636"
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
Un [ComPtr\<T>](comptr-class.md) type ou un type dérivé de lui, pas seulement l’interface représentée par le `ComPtr`.

## <a name="remarks"></a>Notes

Représente une référence à `ComPtr<T>`un objet de type .

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

Nom                               | Description
---------------------------------- | -------------------------------------------------------------------------------------------------------------
[ComPtrRef::ComPtrRef](#comptrref) | Initialise une nouvelle instance `ComPtrRef` de la classe `ComPtrRef` du pointeur spécifié à un autre objet.

### <a name="public-methods"></a>M&#233;thodes publiques

Nom                                                         | Description
------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------
[ComPtrRef::GetAddressOf](#getaddressof)                     | Récupère l’adresse d’un pointeur à `ComPtrRef` l’interface représentée par l’objet actuel.
[ComPtrRef::ReleaseAndGetAddressOf](#releaseandgetaddressof) | Supprime l’objet actuel `ComPtrRef` et renvoie un pointeur à un pointeur `ComPtrRef` à l’interface qui était représentée par l’objet.

### <a name="public-operators"></a>Op&#233;rateurs publics

Nom                                                                     | Description
------------------------------------------------------------------------ | -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
[ComPtrRef::opérateur InterfaceType](#operator-interfacetype-star-star) | Supprime l’objet actuel `ComPtrRef` et renvoie un pointeur à un pointeur `ComPtrRef` à l’interface qui était représentée par l’objet.
[ComPtrRef::opérateur T](#operator-t-star)                               | Retourne la valeur du membre [ptr_](comptrrefbase-class.md#ptr) de données de l’objet ComPtrRef actuel.
[ComPtrRef::opérateur vide](#operator-void-star-star)                   | Supprime l’objet actuel, `ComPtrRef` lance le pointeur à l’interface qui était représentée par l’objet `ComPtrRef` comme pointeur-à-pointer-à, `void`puis retourne le pointeur de casting.
[ComPtrRef::opérateur](#operator-star)                                   | Récupère le pointeur de l’interface `ComPtrRef` représentée par l’objet actuel.
[ComPtrRef::opérateur](#operator-equality)                              | Indique si deux objets `ComPtrRef` sont égaux.
[ComPtrRef::opérateur!](#operator-inequality)                            | Indique si deux objets `ComPtrRef` ne sont pas égaux.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`ComPtrRefBase`

`ComPtrRef`

## <a name="requirements"></a>Spécifications

**En-tête :** client.h

**Espace nom:** Microsoft::WRL::Details

## <a name="comptrrefcomptrref"></a><a name="comptrref"></a>ComPtrRef::ComPtrRef

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

```cpp
ComPtrRef(
   _In_opt_ T* ptr
);
```

### <a name="parameters"></a>Paramètres

*Ptr*<br/>
La valeur sous-jacente d’un autre `ComPtrRef` objet.

### <a name="remarks"></a>Notes

Initialise une nouvelle instance `ComPtrRef` de la classe `ComPtrRef` du pointeur spécifié à un autre objet.

## <a name="comptrrefgetaddressof"></a><a name="getaddressof"></a>ComPtrRef::GetAddressOf

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

```cpp
InterfaceType* const * GetAddressOf() const;
```

### <a name="return-value"></a>Valeur de retour

Adresse d’un pointeur à l’interface représentée par l’objet actuel. `ComPtrRef`

### <a name="remarks"></a>Notes

Récupère l’adresse d’un pointeur à `ComPtrRef` l’interface représentée par l’objet actuel.

## <a name="comptrrefoperator"></a><a name="operator-equality"></a>ComPtrRef::opérateur

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

*Un*<br/>
Référence à un objet `ComPtrRef`.

*B*<br/>
Une référence `ComPtrRef` à un autre objet, ou`void*`un pointeur à un type anonyme ( ).

### <a name="return-value"></a>Valeur de retour

Le premier opérateur cède **vrai** si l’objet *a* est égal à l’objet *b*; autrement, **faux**.

Les deuxième et troisième opérateurs donnent **vrai** si l’objet *a* est égal à **nullptr**; autrement, **faux**.

Les quatrième et cinquième opérateurs donnent **vrai** si l’objet *a* est égal à l’objet *b*; autrement, **faux**.

### <a name="remarks"></a>Notes

Indique si deux objets `ComPtrRef` sont égaux.

## <a name="comptrrefoperator"></a><a name="operator-inequality"></a>ComPtrRef::opérateur!

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

*Un*<br/>
Référence à un objet `ComPtrRef`.

*B*<br/>
Une référence `ComPtrRef` à un autre objet, ou`void*`un pointeur à un objet anonyme ( ).

### <a name="return-value"></a>Valeur de retour

Le premier opérateur cède **vrai** si l’objet *a* n’est pas égal à l’objet *b*; autrement, **faux**.

Les deuxième et troisième opérateurs donnent **vrai** si l’objet *a* n’est pas égal à **nullptr**; autrement, **faux**.

Les quatrième et cinquième opérateurs donnent **vrai** si l’objet *a* n’est pas égal à l’objet *b*; autrement, **faux**.

### <a name="remarks"></a>Notes

Indique si deux objets `ComPtrRef` ne sont pas égaux.

## <a name="comptrrefoperator-interfacetype"></a><a name="operator-interfacetype-star-star"></a>ComPtrRef::opérateur InterfaceType

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

```cpp
operator InterfaceType**();
```

### <a name="remarks"></a>Notes

Supprime l’objet actuel `ComPtrRef` et renvoie un pointeur à un pointeur `ComPtrRef` à l’interface qui était représentée par l’objet.

## <a name="comptrrefoperator"></a><a name="operator-star"></a>ComPtrRef::opérateur

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

```cpp
InterfaceType* operator *();
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers l’interface `ComPtrRef` représentée par l’objet actuel.

### <a name="remarks"></a>Notes

Récupère le pointeur de l’interface `ComPtrRef` représentée par l’objet actuel.

## <a name="comptrrefoperator-t"></a><a name="operator-t-star"></a>ComPtrRef::opérateur T

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

```cpp
operator T*();
```

### <a name="remarks"></a>Notes

Retourne la valeur du [membre ptr_](comptrrefbase-class.md#ptr) de `ComPtrRef` données de l’objet actuel.

## <a name="comptrrefoperator-void"></a><a name="operator-void-star-star"></a>ComPtrRef::opérateur vide\*\*

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

```cpp
operator void**() const;
```

### <a name="remarks"></a>Notes

Supprime l’objet actuel, `ComPtrRef` lance le pointeur à l’interface qui était représentée par l’objet `ComPtrRef` comme pointeur-à-pointer-à, `void`puis retourne le pointeur de casting.

## <a name="comptrrefreleaseandgetaddressof"></a><a name="releaseandgetaddressof"></a>ComPtrRef::ReleaseAndGetAddressOf

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

```cpp
InterfaceType** ReleaseAndGetAddressOf();
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers l’interface qui était `ComPtrRef` représentée par l’objet supprimé.

### <a name="remarks"></a>Notes

Supprime l’objet actuel `ComPtrRef` et renvoie un pointeur à un pointeur `ComPtrRef` à l’interface qui était représentée par l’objet.
