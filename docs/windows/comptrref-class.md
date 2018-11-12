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
ms.openlocfilehash: adfe7a045e0869c13f48770e03de6de10f978a4b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50502934"
---
# <a name="comptrref-class"></a>ComPtrRef (classe)

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

## <a name="syntax"></a>Syntaxe

```cpp
template <typename T>
class ComPtrRef : public ComPtrRefBase<T>;
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Un [ComPtr\<T >](../windows/comptr-class.md) type ou un type dérivé, pas simplement l’interface représentée par le `ComPtr`.

## <a name="remarks"></a>Notes

Représente une référence à un objet de type `ComPtr<T>`.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

Nom                               | Description
---------------------------------- | -------------------------------------------------------------------------------------------------------------
[ComPtrRef::ComPtrRef](#comptrref) | Initialise une nouvelle instance de la `ComPtrRef` classe à partir du pointeur spécifié vers un autre `ComPtrRef` objet.

### <a name="public-methods"></a>M&#233;thodes publiques

Nom                                                         | Description
------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------
[ComPtrRef::GetAddressOf](#getaddressof)                     | Récupère l’adresse d’un pointeur vers l’interface représentée par l’actuel `ComPtrRef` objet.
[ComPtrRef::ReleaseAndGetAddressOf](#releaseandgetaddressof) | Supprime l’actuel `ComPtrRef` de l’objet et retourne un pointeur-à-un-pointeur vers l’interface qui a été représenté par le `ComPtrRef` objet.

### <a name="public-operators"></a>Op&#233;rateurs publics

Nom                                                                     | Description
------------------------------------------------------------------------ | -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
[ComPtrRef::operator InterfaceType **](#operator-interfacetype-star-star) | Supprime l’actuel `ComPtrRef` de l’objet et retourne un pointeur-à-un-pointeur vers l’interface qui a été représenté par le `ComPtrRef` objet.
[ComPtrRef::operator T *](#operator-t-star)                               | Retourne la valeur de la [ptr_](../windows/comptrrefbase-ptr-data-member.md) membre de données de l’objet ComPtrRef actuel.
[ComPtrRef::operator void **](#operator-void-star-star)                   | Supprime l’actuel `ComPtrRef` d’objet, convertit le pointeur vers l’interface qui a été représenté par le `ComPtrRef` objet sous la forme d’un pointeur à pointeur-à `void`, puis retourne le pointeur de cast.
[ComPtrRef::operator *](#operator-star)                                   | Récupère le pointeur vers l’interface représentée par l’actuel `ComPtrRef` objet.
[ComPtrRef::operator ==](#operator-equality)                              | Indique si deux objets `ComPtrRef` sont égaux.
[ComPtrRef::operator ! =](#operator-inequality)                            | Indique si deux objets `ComPtrRef` ne sont pas égaux.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`ComPtrRefBase`

`ComPtrRef`

## <a name="requirements"></a>Configuration requise

**En-tête :** client.h

**Namespace :** Microsoft::WRL::Details

## <a name="comptrref"></a>ComPtrRef::ComPtrRef

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

```cpp
ComPtrRef(
   _In_opt_ T* ptr
);
```

### <a name="parameters"></a>Paramètres

*ptr*<br/>
La valeur sous-jacente d’un autre `ComPtrRef` objet.

### <a name="remarks"></a>Notes

Initialise une nouvelle instance de la `ComPtrRef` classe à partir du pointeur spécifié vers un autre `ComPtrRef` objet.

## <a name="getaddressof"></a>ComPtrRef::GetAddressOf

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

```cpp
InterfaceType* const * GetAddressOf() const;
```

### <a name="return-value"></a>Valeur de retour

Adresse d’un pointeur vers l’interface représentée par l’actuel `ComPtrRef` objet.

### <a name="remarks"></a>Notes

Récupère l’adresse d’un pointeur vers l’interface représentée par l’actuel `ComPtrRef` objet.

## <a name="operator-equality"></a>ComPtrRef::operator ==

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

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

*a*<br/>
Référence à un objet `ComPtrRef`.

*b*<br/>
Une référence à un autre `ComPtrRef` objet, ou un pointeur vers un type anonyme (`void*`).

### <a name="return-value"></a>Valeur de retour

Le premier produit opérateur **true** si objet *un* est égal à l’objet *b*; sinon, **false**.

Les deuxième et troisième opérateurs yield **true** si objet *un* est égal à **nullptr**; sinon, **false**.

Les quatrième et cinquième opérateurs yield **true** si objet *un* est égal à l’objet *b*; sinon, **false**.

### <a name="remarks"></a>Notes

Indique si deux objets `ComPtrRef` sont égaux.

## <a name="operator-inequality"></a>ComPtrRef::operator ! =

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

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

*a*<br/>
Référence à un objet `ComPtrRef`.

*b*<br/>
Une référence à un autre `ComPtrRef` objet, ou un pointeur vers un objet anonyme (`void*`).

### <a name="return-value"></a>Valeur de retour

Le premier produit opérateur **true** si objet *un* n’est pas égal à l’objet *b*; sinon, **false**.

Les deuxième et troisième opérateurs yield **true** si objet *un* n’est pas égal à **nullptr**; sinon, **false**.

Les quatrième et cinquième opérateurs yield **true** si objet *un* n’est pas égal à l’objet *b*; sinon, **false**.

### <a name="remarks"></a>Notes

Indique si deux objets `ComPtrRef` ne sont pas égaux.

## <a name="operator-interfacetype-star-star"></a>ComPtrRef::operator InterfaceType **

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

```cpp
operator InterfaceType**();
```

### <a name="remarks"></a>Notes

Supprime l’actuel `ComPtrRef` de l’objet et retourne un pointeur-à-un-pointeur vers l’interface qui a été représenté par le `ComPtrRef` objet.

## <a name="operator-star"></a>ComPtrRef::operator *

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

```cpp
InterfaceType* operator *();
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers l’interface représentée par l’actuel `ComPtrRef` objet.

### <a name="remarks"></a>Notes

Récupère le pointeur vers l’interface représentée par l’actuel `ComPtrRef` objet.

## <a name="operator-t-star"></a>ComPtrRef::operator T *

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

```cpp
operator T*();
```

### <a name="remarks"></a>Notes

Retourne la valeur de la [ptr_](../windows/comptrrefbase-ptr-data-member.md) membre de données d’actuel `ComPtrRef` objet.

## <a name="operator-void-star-star"></a>ComPtrRef::operator void\*\*

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

```cpp
operator void**() const;
```

### <a name="remarks"></a>Notes

Supprime l’actuel `ComPtrRef` d’objet, convertit le pointeur vers l’interface qui a été représenté par le `ComPtrRef` objet sous la forme d’un pointeur à pointeur-à `void`, puis retourne le pointeur de cast.

## <a name="releaseandgetaddressof"></a>ComPtrRef::ReleaseAndGetAddressOf

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

```cpp
InterfaceType** ReleaseAndGetAddressOf();
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers l’interface qui a été représenté par supprimés `ComPtrRef` objet.

### <a name="remarks"></a>Notes

Supprime l’actuel `ComPtrRef` de l’objet et retourne un pointeur-à-un-pointeur vers l’interface qui a été représenté par le `ComPtrRef` objet.
