---
title: ComPtr (classe)
ms.date: 07/26/2019
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::ComPtr
- client/Microsoft::WRL::ComPtr::As
- client/Microsoft::WRL::ComPtr::AsIID
- client/Microsoft::WRL::ComPtr::AsWeak
- client/Microsoft::WRL::ComPtr::Attach
- client/Microsoft::WRL::ComPtr::ComPtr
- client/Microsoft::WRL::ComPtr::CopyTo
- client/Microsoft::WRL::ComPtr::Detach
- client/Microsoft::WRL::ComPtr::Get
- client/Microsoft::WRL::ComPtr::GetAddressOf
- client/Microsoft::WRL::ComPtr::InternalAddRef
- client/Microsoft::WRL::ComPtr::InternalRelease
- client/Microsoft::WRL::ComPtr::operator&
- client/Microsoft::WRL::ComPtr::operator->
- client/Microsoft::WRL::ComPtr::operator=
- client/Microsoft::WRL::ComPtr::operator==
- client/Microsoft::WRL::ComPtr::operator!=
- client/Microsoft::WRL::ComPtr::operator Microsoft::WRL::Details::BoolType
- client/Microsoft::WRL::ComPtr::ptr_
- client/Microsoft::WRL::ComPtr::ReleaseAndGetAddressOf
- client/Microsoft::WRL::ComPtr::Reset
- client/Microsoft::WRL::ComPtr::Swap
- client/Microsoft::WRL::ComPtr::~ComPtr
helpviewer_keywords:
- Microsoft::WRL::ComPtr class
- Microsoft::WRL::ComPtr::As method
- Microsoft::WRL::ComPtr::AsIID method
- Microsoft::WRL::ComPtr::AsWeak method
- Microsoft::WRL::ComPtr::Attach method
- Microsoft::WRL::ComPtr::ComPtr, constructor
- Microsoft::WRL::ComPtr::CopyTo method
- Microsoft::WRL::ComPtr::Detach method
- Microsoft::WRL::ComPtr::Get method
- Microsoft::WRL::ComPtr::GetAddressOf method
- Microsoft::WRL::ComPtr::InternalAddRef method
- Microsoft::WRL::ComPtr::InternalRelease method
- Microsoft::WRL::ComPtr::operator& operator
- Microsoft::WRL::ComPtr::operator-> operator
- Microsoft::WRL::ComPtr::operator= operator
- Microsoft::WRL::ComPtr::operator== operator
- Microsoft::WRL::ComPtr::operator!= operator
- Microsoft::WRL::ComPtr::operator Microsoft::WRL::Details::BoolType operator
- Microsoft::WRL::ComPtr::ptr_ data member
- Microsoft::WRL::ComPtr::ReleaseAndGetAddressOf method
- Microsoft::WRL::ComPtr::Reset method
- Microsoft::WRL::ComPtr::Swap method
- Microsoft::WRL::ComPtr::~ComPtr, destructor
ms.assetid: a6551902-6819-478a-8df7-b6f312ab1fb0
ms.openlocfilehash: 1e20a991c8f32027aeea6a17df0534aa6e1c2c43
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69498415"
---
# <a name="comptr-class"></a>ComPtr (classe)

Crée un type de *pointeur intelligent* représentant l'interface spécifiée par le paramètre de modèle. `ComPtr` met à jour automatiquement un décompte de références pour le pointeur d'interface sous-jacent et libère l'interface lorsque le décompte de références atteint zéro.

## <a name="syntax"></a>Syntaxe

```cpp
template <typename T>
class ComPtr;

template<class T>
friend class ComPtr;
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Interface que `ComPtr` représente.

*U*<br/>
Classe à laquelle le actuel `ComPtr` est un Friend. (Le modèle qui utilise ce paramètre est protégé).

## <a name="remarks"></a>Notes

`ComPtr<>`déclare un type qui représente le pointeur d’interface sous-jacent. Utilisez `ComPtr<>` pour déclarer une variable, puis utilisez l’opérateur d’accès aux membres Arrow`->`() pour accéder à une fonction membre d’interface.

Pour plus d’informations sur les pointeurs intelligents, consultez la sous-section «pointeurs intelligents COM» de la rubrique relative aux [pratiques de codage com](/windows/win32/LearnWin32/com-coding-practices) dans MSDN Library.

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

Nom            | Description
--------------- | ---------------------------------------------------------------
`InterfaceType` | Synonyme du type spécifié par le paramètre de modèle *T* .

### <a name="public-constructors"></a>Constructeurs publics

Nom                             | Description
-------------------------------- | --------------------------------------------------------------------------------------------------------------------
[ComPtr::ComPtr](#comptr)        | Initialise une nouvelle instance de la classe `ComPtr`. Les surcharges fournissent des constructeurs par défaut, de copie, de déplacement et de conversion.
[ComPtr:: ~ ComPtr](#tilde-comptr) | Déinitialise une instance de `ComPtr`.

### <a name="public-methods"></a>M&#233;thodes publiques

Nom                                                      | Description
--------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
[ComPtr:: As](#as)                                         | Retourne un `ComPtr` objet qui représente l’interface identifiée par le paramètre de modèle spécifié.
[ComPtr::AsIID](#asiid)                                   | Retourne un `ComPtr` objet qui représente l’interface identifiée par l’ID d’interface spécifié.
[ComPtr:: Asweak,](#asweak)                                 | Récupère une référence faible à l’objet actif.
[ComPtr::Attach](#attach)                                 | Associe `ComPtr` ce au type d’interface spécifié par le paramètre de type de modèle actuel.
[ComPtr::CopyTo](#copyto)                                 | Copie l’interface actuelle ou spécifiée associée à ce `ComPtr` vers le pointeur de sortie spécifié.
[ComPtr::Detach](#detach)                                 | Dissocie ce `ComPtr` de l’interface qu’il représente.
[ComPtr:: obtient](#get)                                       | Récupère un pointeur vers l’interface associée à ce `ComPtr`.
[ComPtr::GetAddressOf](#getaddressof)                     | Récupère l’adresse du membre de données [PTR_](#ptr) , qui contient un pointeur vers l’interface représentée par ce `ComPtr`.
[ComPtr::ReleaseAndGetAddressOf](#releaseandgetaddressof) | Libère l’interface associée à ce `ComPtr` , puis récupère l’adresse du membre de données [PTR_](#ptr) , qui contient un pointeur vers l’interface qui a été libérée.
[ComPtr::Reset](#reset)                                   | Libère toutes les références pour le pointeur vers l’interface associée à ce `ComPtr`.
[ComPtr::Swap](#swap)                                     | Échange l’interface gérée par le `ComPtr` actuel avec l’interface gérée par `ComPtr`le spécifié.

### <a name="protected-methods"></a>Méthodes protégées

Nom                                        | Description
------------------------------------------- | --------------------------------------------------------------------------------
[ComPtr::InternalAddRef](#internaladdref)   | Incrémente le décompte de références de l’interface associée `ComPtr`à ce.
[ComPtr::InternalRelease](#internalrelease) | Exécute une opération de mise en service COM sur l’interface `ComPtr`associée à ce.

### <a name="public-operators"></a>Op&#233;rateurs publics

Nom                                                                                           | Description
---------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------
[ComPtr:: operator &](#operator-ampersand)                                                       | Récupère l’adresse du actuel `ComPtr`.
[ComPtr::operator->](#operator-arrow)                                                          | Récupère un pointeur vers le type spécifié par le paramètre de modèle actuel.
[ComPtr::operator=](#operator-assign)                                                          | Assigne une valeur à l’objet `ComPtr`actuel.
[ComPtr::operator==](#operator-equality)                                                       | Indique si deux objets `ComPtr` sont égaux.
[ComPtr::operator!=](#operator-inequality)                                                     | Indique si deux objets `ComPtr` ne sont pas égaux.
[ComPtr:: Operator Microsoft:: WRL::D étails:: Booltype,](#operator-microsoft-wrl-details-booltype) | Indique si un `ComPtr` gère la durée de vie des objets d’une interface.

### <a name="protected-data-members"></a>Membres de données protégés

Nom                 | Description
-------------------- | ------------------------------------------------------------------------------------------
[ComPtr::ptr_](#ptr) | Contient un pointeur vers l’interface qui est associée à et gérée par ce `ComPtr`.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`ComPtr`

## <a name="requirements"></a>Configuration requise

**En-tête :** client.h

**Espace de noms :** Microsoft:: WRL

## <a name="tilde-comptr"></a>ComPtr:: ~ ComPtr

Déinitialise une instance de `ComPtr`.

```cpp
WRL_NOTHROW ~ComPtr();
```

## <a name="as"></a>ComPtr:: As

Retourne un `ComPtr` objet qui représente l’interface identifiée par le paramètre de modèle spécifié.

```cpp
template<typename U>
HRESULT As(
   _Out_ ComPtr<U>* p
) const;

template<typename U>
HRESULT As(
   _Out_ Details::ComPtrRef<ComPtr<U>> p
) const;
```

### <a name="parameters"></a>Paramètres

*U*<br/>
Interface à représenter par le paramètre *p*.

*p*<br/>
Objet qui représente l’interface spécifiée par le paramètre *U.* `ComPtr` Le paramètre *p* ne doit pas faire référence `ComPtr` à l’objet actuel.

### <a name="remarks"></a>Notes

Le premier modèle est le formulaire que vous devez utiliser dans votre code. Le deuxième modèle est une spécialisation d’assistance interne qui prend en charge les fonctionnalités du langage C++ telles que le mot clé de déduction de type [auto](../../cpp/auto-cpp.md) .

### <a name="return-value"></a>Valeur de retour

S_OK si l'opération réussit. Sinon, une valeur HRESULT indique l'erreur.

## <a name="asiid"></a>ComPtr::AsIID

Retourne un `ComPtr` objet qui représente l’interface identifiée par l’ID d’interface spécifié.

```cpp
WRL_NOTHROW HRESULT AsIID(
   REFIID riid,
   _Out_ ComPtr<IUnknown>* p
) const;
```

### <a name="parameters"></a>Paramètres

*riid*<br/>
ID d’interface.

*p*<br/>
Si l’objet a une interface dont l’ID est égal à *riid*, pointeur doublement indirect vers l’interface spécifiée par le paramètre *riid* ; Sinon, pointeur vers `IUnknown`.

### <a name="return-value"></a>Valeur de retour

S_OK si l'opération réussit. Sinon, une valeur HRESULT indique l'erreur.

## <a name="asweak"></a>ComPtr:: Asweak,

Récupère une référence faible à l’objet actif.

```cpp
HRESULT AsWeak(
   _Out_ WeakRef* pWeakRef
);
```

### <a name="parameters"></a>Paramètres

*pWeakRef*<br/>
Lorsque cette opération est terminée, pointeur vers un objet de référence faible.

### <a name="return-value"></a>Valeur de retour

S_OK si l'opération réussit. Sinon, une valeur HRESULT indique l'erreur.

## <a name="attach"></a>ComPtr::Attach

Associe `ComPtr` ce au type d’interface spécifié par le paramètre de type de modèle actuel.

```cpp
void Attach(
   _In_opt_ InterfaceType* other
);
```

### <a name="parameters"></a>Paramètres

*other*<br/>
Type d’interface.

## <a name="comptr"></a>ComPtr::ComPtr

Initialise une nouvelle instance de la classe `ComPtr`. Les surcharges fournissent des constructeurs par défaut, de copie, de déplacement et de conversion.

```cpp
WRL_NOTHROW ComPtr();

WRL_NOTHROW ComPtr(
   decltype(__nullptr)
);

template<class U>
WRL_NOTHROW ComPtr(
   _In_opt_ U *other
);

WRL_NOTHROW ComPtr(
   const ComPtr& other
);

template<class U>
WRL_NOTHROW ComPtr(
   const ComPtr<U> &other,
   typename ENABLE_IF<__is_convertible_to(U*, T*), void *>
);

WRL_NOTHROW ComPtr(
   _Inout_ ComPtr &&other
);

template<class U>
WRL_NOTHROW ComPtr(
   _Inout_ ComPtr<U>&& other, typename ENABLE_IF<__is_convertible_to(U*, T*), void *>
);
```

### <a name="parameters"></a>Paramètres

*U*<br/>
Type de l' *autre* paramètre.

*other*<br/>
Objet de type *U*.

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

Le premier constructeur est le constructeur par défaut, qui implictly crée un objet vide. Le deuxième constructeur spécifie [__nullptr](../../extensions/nullptr-cpp-component-extensions.md), qui crée explicitement un objet vide.

Le troisième constructeur crée un objet à partir de l’objet spécifié par un pointeur. Le ComPtr est maintenant propriétaire de la mémoire pointée et gère un décompte de références.

Les quatrième et cinquième constructeurs sont des constructeurs de copie. Le cinquième constructeur copie un objet s’il est convertible dans le type actuel.

Les sixième et septième constructeurs sont des constructeurs de déplacement. Le septième constructeur déplace un objet s’il est convertible dans le type actuel.

## <a name="copyto"></a>ComPtr::CopyTo

Copie l’interface actuelle ou spécifiée associée à ce `ComPtr` vers le pointeur spécifié.

```cpp
HRESULT CopyTo(
   _Deref_out_ InterfaceType** ptr
);

HRESULT CopyTo(
   REFIID riid,
   _Deref_out_ void** ptr
) const;

template<typename U>
HRESULT CopyTo(
   _Deref_out_ U** ptr
) const;
```

### <a name="parameters"></a>Paramètres

*U*<br/>
Un nom de type.

*ptr*<br/>
Lorsque cette opération est terminée, il s’agit d’un pointeur vers l’interface demandée.

*riid*<br/>
ID d’interface.

### <a name="return-value"></a>Valeur de retour

S_OK en cas de réussite; Sinon, HRESULT qui indique la raison de l' `QueryInterface` échec de l’opération implicite.

### <a name="remarks"></a>Notes

La première fonction retourne une copie d’un pointeur vers l’interface associée à ce `ComPtr`. Cette fonction retourne toujours S_OK.

La deuxième fonction effectue une `QueryInterface` opération sur l’interface associée à ce `ComPtr` pour l’interface spécifiée par le paramètre *riid* .

La troisième fonction effectue une `QueryInterface` opération sur l’interface associée à ce `ComPtr` pour l’interface sous-jacente du paramètre *U* .

## <a name="detach"></a>ComPtr::Detach

Dissocie cet `ComPtr` objet de l’interface qu’il représente.

```cpp
T* Detach();
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers l’interface qui a été représentée par cet `ComPtr` objet.

## <a name="get"></a>ComPtr:: obtient

Récupère un pointeur vers l’interface associée à ce `ComPtr`.

```cpp
T* Get() const;
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers l’interface associée à ce `ComPtr`.

## <a name="getaddressof"></a>ComPtr::GetAddressOf

Récupère l’adresse du membre de données [PTR_](#ptr) , qui contient un pointeur vers l’interface représentée par ce `ComPtr`.

```cpp
T* const* GetAddressOf() const;
T** GetAddressOf();
```

### <a name="return-value"></a>Valeur de retour

Adresse d’une variable.

## <a name="internaladdref"></a>ComPtr::InternalAddRef

Incrémente le décompte de références de l’interface associée `ComPtr`à ce.

```cpp
void InternalAddRef() const;
```

### <a name="remarks"></a>Notes

Cette méthode est protégée.

## <a name="internalrelease"></a>ComPtr::InternalRelease

Exécute une opération de mise en service COM sur l’interface `ComPtr`associée à ce.

```cpp
void InternalRelease();
```

### <a name="remarks"></a>Notes

Cette méthode est protégée.

## <a name="operator-ampersand"></a>ComPtr::operator&amp;

Libère l’interface associée à cet `ComPtr` objet, puis récupère l’adresse de l' `ComPtr` objet.

```cpp
Details::ComPtrRef<WeakRef> operator&()

const Details::ComPtrRef<const WeakRef> operator&() const
```

### <a name="return-value"></a>Valeur de retour

Référence faible à l’objet actuel `ComPtr`.

### <a name="remarks"></a>Notes

Cette méthode diffère de [ComPtr:: getaddressof,](#getaddressof) dans le fait que cette méthode libère une référence au pointeur d’interface. Utilisez `ComPtr::GetAddressOf` lorsque vous avez besoin de l’adresse du pointeur d’interface, mais que vous ne souhaitez pas libérer cette interface.

## <a name="operator-arrow"></a>ComPtr:: Operator-&gt;

Récupère un pointeur vers le type spécifié par le paramètre de modèle actuel.

```cpp
WRL_NOTHROW Microsoft::WRL::Details::RemoveIUnknown<InterfaceType>* operator->() const;
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers le type spécifié par le nom du type de modèle actuel.

### <a name="remarks"></a>Notes

Cette fonction d’assistance supprime la surcharge inutile provoquée par l’utilisation de la macro STDMETHOD. Cette fonction effectue `IUnknown` des `private` types au `virtual`lieu de.

## <a name="operator-assign"></a>ComPtr::operator=

Assigne une valeur à l’objet `ComPtr`actuel.

```cpp
WRL_NOTHROW ComPtr& operator=(
   decltype(__nullptr)
);
WRL_NOTHROW ComPtr& operator=(
   _In_opt_ T *other
);
template <typename U>
WRL_NOTHROW ComPtr& operator=(
   _In_opt_ U *other
);
WRL_NOTHROW ComPtr& operator=(
   const ComPtr &other
);
template<class U>
WRL_NOTHROW ComPtr& operator=(
   const ComPtr<U>& other
);
WRL_NOTHROW ComPtr& operator=(
   _Inout_ ComPtr &&other
);
template<class U>
WRL_NOTHROW ComPtr& operator=(
   _Inout_ ComPtr<U>&& other
);
```

### <a name="parameters"></a>Paramètres

*U*<br/>
Une classe.

*other*<br/>
Une référence de pointeur, de référence ou rvalue à un type ou `ComPtr`un autre.

### <a name="return-value"></a>Valeur de retour

Référence à l’objet actuel `ComPtr`.

### <a name="remarks"></a>Notes

La première version de cet opérateur assigne une valeur vide à l’objet `ComPtr`actuel.

Dans la deuxième version, si le pointeur d’interface Assigning n’est pas le même `ComPtr` que le pointeur d’interface actuel, le deuxième pointeur d’interface `ComPtr`est assigné à l’objet actuel.

Dans la troisième version, le pointeur d’interface Assigning est assigné à `ComPtr`l’objet actuel.

Dans la quatrième version, si le pointeur d’interface de la valeur d’assignation n’est pas le même que `ComPtr` le pointeur d’interface actuel, le deuxième pointeur d’interface est `ComPtr`assigné à l’objet actuel.

La cinquième version est un opérateur de copie; une référence à un `ComPtr` est assignée à `ComPtr`l’objet actuel.

La sixième version est un opérateur de copie qui utilise la sémantique de déplacement. Référence rvalue à un `ComPtr` si tout type est Cast statique, puis assigné à l’objet actuel. `ComPtr`

La septième version est un opérateur de copie qui utilise la sémantique de déplacement. une référence rvalue à un `ComPtr` de type *U* est un cast statique, puis assigné à l' `ComPtr`objet actuel.

## <a name="operator-equality"></a>ComPtr::operator==

Indique si deux objets `ComPtr` sont égaux.

```cpp
bool operator==(
   const ComPtr<T>& a,
   const ComPtr<U>& b
);

bool operator==(
   const ComPtr<T>& a,
   decltype(__nullptr)
);

bool operator==(
   decltype(__nullptr),
   const ComPtr<T>& a
);
```

### <a name="parameters"></a>Paramètres

*a*<br/>
Référence à un objet `ComPtr`.

*b*<br/>
Référence à un autre `ComPtr` objet.

### <a name="return-value"></a>Valeur de retour

Le premier `true` opérateur produit si l’objet *a* est égal à l’objet *b*; sinon `false`,.

Le deuxième et le troisième opérateur `true` produisent si l’objet *a* est `nullptr`égal à; `false`sinon,.

## <a name="operator-inequality"></a>ComPtr::operator!=

Indique si deux objets `ComPtr` ne sont pas égaux.

```cpp
bool operator!=(
   const ComPtr<T>& a,
   const ComPtr<U>& b
);

bool operator!=(
   const ComPtr<T>& a,
   decltype(__nullptr)
);

bool operator!=(
   decltype(__nullptr),
   const ComPtr<T>& a
);
```

### <a name="parameters"></a>Paramètres

*a*<br/>
Référence à un objet `ComPtr`.

*b*<br/>
Référence à un autre `ComPtr` objet.

### <a name="return-value"></a>Valeur de retour

Le premier `true` opérateur produit si l’objet *a* n’est pas égal à l’objet *b*; `false`sinon,.

Le deuxième et le troisième opérateur `true` produisent si l’objet *a* n’est `nullptr`pas égal à `false`; sinon,.

## <a name="operator-microsoft-wrl-details-booltype"></a>ComPtr:: Operator Microsoft:: WRL::D étails:: Booltype,

Indique si un `ComPtr` gère la durée de vie des objets d’une interface.

```cpp
WRL_NOTHROW operator Microsoft::WRL::Details::BoolType() const;
```

### <a name="return-value"></a>Valeur de retour

Si une interface est associée à `ComPtr`, il s’agit de l’adresse du membre de données [BoolStruct:: Member](boolstruct-structure.md#member) ; sinon,. `nullptr`

## <a name="ptr"></a>ComPtr::ptr_

Contient un pointeur vers l’interface qui est associée à et gérée par ce `ComPtr`.

```cpp
InterfaceType *ptr_;
```

### <a name="remarks"></a>Notes

`ptr_`est un membre de données interne et protégé.

## <a name="releaseandgetaddressof"></a>ComPtr::ReleaseAndGetAddressOf

Libère l’interface associée à ce `ComPtr` , puis récupère l’adresse du membre de données [PTR_](#ptr) , qui contient un pointeur vers l’interface qui a été libérée.

```cpp
T** ReleaseAndGetAddressOf();
```

### <a name="return-value"></a>Valeur de retour

Adresse du membre de données [PTR_](#ptr) de ce `ComPtr`.

## <a name="reset"></a>ComPtr::Reset

Libère toutes les références pour le pointeur vers l’interface associée à ce `ComPtr`.

```cpp
unsigned long Reset();
```

### <a name="return-value"></a>Valeur de retour

Nombre de références éventuellement publiées.

## <a name="swap"></a>ComPtr::Swap

Échange l’interface gérée par le `ComPtr` actuel avec l’interface gérée par `ComPtr`le spécifié.

```cpp
void Swap(
   _Inout_ ComPtr&& r
);

void Swap(
   _Inout_ ComPtr& r
);
```

### <a name="parameters"></a>Paramètres

*r*<br/>
`ComPtr`

