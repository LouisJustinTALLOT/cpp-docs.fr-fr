---
title: ComPtr (classe)
ms.date: 10/01/2018
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
ms.openlocfilehash: da6d0761b60257bc4b0232123d179e9c04465844
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54336030"
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
L’interface qui le `ComPtr` représente.

*U*<br/>
Une classe à laquelle actuel `ComPtr` soit un assembly friend. (Le modèle qui utilise ce paramètre est protégé).

## <a name="remarks"></a>Notes

`ComPtr<>` déclare un type qui représente le pointeur d’interface sous-jacent. Utilisez `ComPtr<>` pour déclarer une variable, puis utiliser l’opérateur member-access flèche (`->`) pour accéder à une fonction membre d’interface.

Pour plus d’informations sur les pointeurs intelligents, consultez la sous-section « Pointeurs intelligents COM » le [COM Coding Practices](/windows/desktop/LearnWin32/com-coding-practices) rubrique dans MSDN Library.

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

Nom            | Description
--------------- | ---------------------------------------------------------------
`InterfaceType` | Un synonyme du type spécifié par le *T* paramètre de modèle.

### <a name="public-constructors"></a>Constructeurs publics

Nom                             | Description
-------------------------------- | --------------------------------------------------------------------------------------------------------------------
[ComPtr::ComPtr](#comptr)        | Initialise une nouvelle instance de la classe `ComPtr`. Les surcharges fournissent des constructeurs par défaut, de copie, de déplacement et de conversion.
[ComPtr::~ComPtr](#tilde-comptr) | Annule l’initialisation d’une instance de `ComPtr`.

### <a name="public-methods"></a>M&#233;thodes publiques

Nom                                                      | Description
--------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
[ComPtr::As](#as)                                         | Retourne un `ComPtr` objet qui représente l’interface identifiée par le paramètre de modèle spécifié.
[ComPtr::AsIID](#asiid)                                   | Retourne un `ComPtr` objet qui représente l’interface identifiée par l’ID de l’interface spécifiée.
[ComPtr::AsWeak](#asweak)                                 | Récupère une référence faible à l’objet actif.
[ComPtr::Attach](#attach)                                 | Cela associe `ComPtr` avec le type d’interface spécifié par le paramètre de type de modèle actuel.
[ComPtr::CopyTo](#copyto)                                 | Copie de l’interface actuelle ou spécifiée associée à cet `ComPtr` vers le pointeur de sortie spécifié.
[ComPtr::Detach](#detach)                                 | Il dissocie `ComPtr` à partir de l’interface qu’elle représente.
[ComPtr::Get](#get)                                       | Récupère un pointeur vers l’interface qui est associé à ce `ComPtr`.
[ComPtr::GetAddressOf](#getaddressof)                     | Récupère l’adresse de la [ptr_](#ptr) membre de données, qui contient un pointeur vers l’interface représentée par ce `ComPtr`.
[ComPtr::ReleaseAndGetAddressOf](#releaseandgetaddressof) | Libère l’interface associée à cet `ComPtr` , puis récupère l’adresse de la [ptr_](#ptr) membre de données, qui contient un pointeur vers l’interface qui a été publiée.
[ComPtr::Reset](#reset)                                   | Libère toutes les références pour le pointeur vers l’interface qui est associé à ce `ComPtr`.
[ComPtr::Swap](#swap)                                     | Échange l’interface gérée par l’actuel `ComPtr` avec l’interface gérée par le `ComPtr`.

### <a name="protected-methods"></a>Méthodes protégées

Nom                                        | Description
------------------------------------------- | --------------------------------------------------------------------------------
[ComPtr::InternalAddRef](#internaladdref)   | Incrémente le décompte de références de l’interface associée à cet `ComPtr`.
[ComPtr::InternalRelease](#internalrelease) | Effectue une opération de libération de COM sur l’interface associée à cet `ComPtr`.

### <a name="public-operators"></a>Op&#233;rateurs publics

Nom                                                                                           | Description
---------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------
[ComPtr::operator &](#operator-ampersand)                                                       | Récupère l’adresse de l’actuel `ComPtr`.
[ComPtr::operator->](#operator-arrow)                                                          | Récupère un pointeur vers le type spécifié par le paramètre de modèle actuel.
[ComPtr::operator=](#operator-assign)                                                          | Assigne une valeur à actuel `ComPtr`.
[ComPtr::operator==](#operator-equality)                                                       | Indique si deux objets `ComPtr` sont égaux.
[ComPtr::operator!=](#operator-inequality)                                                     | Indique si deux objets `ComPtr` ne sont pas égaux.
[ComPtr::operator Microsoft::WRL::Details::BoolType](#operator-microsoft-wrl-details-booltype) | Indique ou non un `ComPtr` gère la durée de vie d’une interface.

### <a name="protected-data-members"></a>Membres de données protégés

Name                 | Description
-------------------- | ------------------------------------------------------------------------------------------
[ComPtr::ptr_](#ptr) | Contient un pointeur vers l’interface qui est associé et géré par ce `ComPtr`.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`ComPtr`

## <a name="requirements"></a>Spécifications

**En-tête :** client.h

**Espace de noms :** Microsoft::wrl

## <a name="tilde-comptr"></a>ComPtr::~ComPtr

Annule l’initialisation d’une instance de `ComPtr`.

```cpp
WRL_NOTHROW ~ComPtr();
```

## <a name="as"></a>ComPtr::As

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
L’interface pour être représentée par le paramètre *p*.

*p*<br/>
Un `ComPtr` objet qui représente l’interface spécifiée par le paramètre *U*. Paramètre *p* ne doit pas faire référence à l’actuel `ComPtr` objet.

### <a name="remarks"></a>Notes

Le premier modèle est le formulaire que vous devez utiliser dans votre code. Le deuxième modèle est une spécialisation d’assistance interne qui prend en charge les fonctionnalités du langage C++ telles que le mot clé de déduction de type [auto](../../cpp/auto-cpp.md) .

### <a name="return-value"></a>Valeur de retour

S_OK si l'opération réussit. Sinon, une valeur HRESULT indique l'erreur.

## <a name="asiid"></a>ComPtr::AsIID

Retourne un `ComPtr` objet qui représente l’interface identifiée par l’ID de l’interface spécifiée.

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
Si l’objet a une interface dont l’ID est égal à *riid*, un pointeur doublement indirect vers l’interface spécifiée par le *riid* paramètre ; sinon, un pointeur vers `IUnknown`.

### <a name="return-value"></a>Valeur de retour

S_OK si l'opération réussit. Sinon, une valeur HRESULT indique l'erreur.

## <a name="asweak"></a>ComPtr::AsWeak

Récupère une référence faible à l’objet actif.

```cpp
HRESULT AsWeak(
   _Out_ WeakRef* pWeakRef
);
```

### <a name="parameters"></a>Paramètres

*pWeakRef*<br/>
Lorsque cette opération se termine, un pointeur vers un objet de référence faible.

### <a name="return-value"></a>Valeur de retour

S_OK si l'opération réussit. Sinon, une valeur HRESULT indique l'erreur.

## <a name="attach"></a>ComPtr::Attach

Cela associe `ComPtr` avec le type d’interface spécifié par le paramètre de type de modèle actuel.

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
   typename ENABLE_IF<__is_convertible_to(U*,
   T*),
   void *>;
WRL_NOTHROW ComPtr(
   _Inout_ ComPtr &&other
);
template<class U>
WRL_NOTHROW ComPtr(
   _Inout_ ComPtr<U>&& other,
   typename ENABLE_IF<__is_convertible_to(U*,
   T*),
   void *>;
```

### <a name="parameters"></a>Paramètres

*U*<br/>
Le type de la *autres* paramètre.

*other*<br/>
Un objet de type *U*.

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

Le premier constructeur est le constructeur par défaut, l’implicitement crée un objet vide. Le deuxième constructeur spécifie [__nullptr](../nullptr-cpp-component-extensions.md), ce qui crée explicitement un objet vide.

Le troisième constructeur crée un objet à partir de l’objet spécifié par un pointeur.

Les quatrième et cinquième constructeurs sont des constructeurs de copie. Le cinquième constructeur copie un objet s’il est converti vers le type actuel.

Les sixième et septième constructeurs sont des constructeurs de déplacement. Le septième constructeur déplace un objet s’il est converti vers le type actuel.

## <a name="copyto"></a>ComPtr::CopyTo

Copie de l’interface actuelle ou spécifiée associée à cet `ComPtr` pour le pointeur spécifié.

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
Lorsque cette opération se termine, un pointeur vers l’interface demandée.

*riid*<br/>
ID d’interface.

### <a name="return-value"></a>Valeur de retour

S_OK en cas de réussite ; Sinon, un HRESULT qui indique la raison pour laquelle le caractère implicite `QueryInterface` échouée de l’opération.

### <a name="remarks"></a>Notes

La première fonction retourne une copie d’un pointeur vers l’interface associée à cet `ComPtr`. Cette fonction retourne toujours S_OK.

La deuxième fonction effectue une `QueryInterface` opération sur l’interface associée à cet `ComPtr` pour l’interface spécifiée par le *riid* paramètre.

La troisième fonction effectue une `QueryInterface` opération sur l’interface associée à cet `ComPtr` pour l’interface sous-jacente de la *U* paramètre.

## <a name="detach"></a>ComPtr::Detach

Il dissocie `ComPtr` objet à partir de l’interface qu’elle représente.

```cpp
T* Detach();
```

### <a name="return-value"></a>Valeur de retour

Un pointeur vers l’interface qui a été représenté par cet `ComPtr` objet.

## <a name="get"></a>ComPtr::Get

Récupère un pointeur vers l’interface qui est associé à ce `ComPtr`.

```cpp
T* Get() const;
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers l’interface qui est associé à ce `ComPtr`.

## <a name="getaddressof"></a>ComPtr::GetAddressOf

Récupère l’adresse de la [ptr_](#ptr) membre de données, qui contient un pointeur vers l’interface représentée par ce `ComPtr`.

```cpp
T* const* GetAddressOf() const;
T** GetAddressOf();
```

### <a name="return-value"></a>Valeur de retour

L’adresse d’une variable.

## <a name="internaladdref"></a>ComPtr::InternalAddRef

Incrémente le décompte de références de l’interface associée à cet `ComPtr`.

```cpp
void InternalAddRef() const;
```

### <a name="remarks"></a>Notes

Cette méthode est protégée.

## <a name="internalrelease"></a>ComPtr::InternalRelease

Effectue une opération de libération de COM sur l’interface associée à cet `ComPtr`.

```cpp
void InternalRelease();
```

### <a name="remarks"></a>Notes

Cette méthode est protégée.

## <a name="operator-ampersand"></a>ComPtr::operator&amp;

Libère l’interface associée à cet `ComPtr` de l’objet, puis récupère l’adresse de la `ComPtr` objet.

```cpp
Details::ComPtrRef<WeakRef> operator&()

const Details::ComPtrRef<const WeakRef> operator&() const
```

### <a name="return-value"></a>Valeur de retour

Une référence faible à actuel `ComPtr`.

### <a name="remarks"></a>Notes

Cette méthode diffère de [ComPtr::GetAddressOf](#getaddressof) dans la mesure où cette méthode libère une référence au pointeur d’interface. Utilisez `ComPtr::GetAddressOf` lorsque vous nécessitent l’adresse du pointeur d’interface, mais ne souhaitez pas libérer cette interface.

## <a name="operator-arrow"></a>ComPtr::operator-&gt;

Récupère un pointeur vers le type spécifié par le paramètre de modèle actuel.

```cpp
WRL_NOTHROW Microsoft::WRL::Details::RemoveIUnknown<InterfaceType>* operator->() const;
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers le type spécifié par le nom de type de modèle actuel.

### <a name="remarks"></a>Notes

Cette fonction d’assistance supprime provoquée par l’utilisation de la macro STDMETHOD une surcharge inutile. Cette fonction effectue `IUnknown` types `private` au lieu de `virtual`.

## <a name="operator-assign"></a>ComPtr::operator=

Assigne une valeur à actuel `ComPtr`.

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
Un pointeur, une référence ou une référence rvalue à un type ou un autre `ComPtr`.

### <a name="return-value"></a>Valeur de retour

Une référence à l’actuel `ComPtr`.

### <a name="remarks"></a>Notes

La première version de cet opérateur assigne une valeur vide à actuel `ComPtr`.

Dans la deuxième version, si le pointeur d’interface affectation n’est pas le même que l’actuel `ComPtr` pointeur d’interface, le deuxième pointeur d’interface est affecté à l’actuel `ComPtr`.

Dans la troisième version, le pointeur d’interface affectation est affecté au actuel `ComPtr`.

Dans la quatrième version, si le pointeur d’interface de la valeur d’assignation n’est pas le même que l’actuel `ComPtr` pointeur d’interface, le deuxième pointeur d’interface est affecté à l’actuel `ComPtr`.

La cinquième version est un opérateur copie ; une référence à un `ComPtr` est affectée à l’actuel `ComPtr`.

La sixième version est un opérateur de copie qui utilise la sémantique ; de déplacement une référence rvalue à un `ComPtr` si n’importe quel type est statique, effectuer un cast, puis affecté au cours `ComPtr`.

La septième version est un opérateur de copie qui utilise la sémantique ; de déplacement une référence rvalue à un `ComPtr` de type *U* est statique converti puis et assignée à actuel `ComPtr`.

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
Une référence à un autre `ComPtr` objet.

### <a name="return-value"></a>Valeur de retour

Le premier produit opérateur `true` si objet *un* est égal à l’objet *b*; sinon, `false`.

Les deuxième et troisième opérateurs yield `true` si objet *un* est égal à `nullptr`; sinon, `false`.

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
Une référence à un autre `ComPtr` objet.

### <a name="return-value"></a>Valeur de retour

Le premier produit opérateur `true` si objet *un* n’est pas égal à l’objet *b*; sinon, `false`.

Les deuxième et troisième opérateurs yield `true` si objet *un* n’est pas égal à `nullptr`; sinon, `false`.

## <a name="operator-microsoft-wrl-details-booltype"></a>ComPtr::operator Microsoft::WRL::Details::BoolType

Indique ou non un `ComPtr` gère la durée de vie d’une interface.

```cpp
WRL_NOTHROW operator Microsoft::WRL::Details::BoolType() const;
```

### <a name="return-value"></a>Valeur de retour

Si une interface est associée à ce `ComPtr`, l’adresse de la [BoolStruct::Member](boolstruct-structure.md#member) membre de données ; sinon, `nullptr`.

## <a name="ptr"></a>ComPtr::ptr_

Contient un pointeur vers l’interface qui est associé et géré par ce `ComPtr`.

```cpp
InterfaceType *ptr_;
```

### <a name="remarks"></a>Notes

`ptr_` est un membre de données protégée, interne.

## <a name="releaseandgetaddressof"></a>ComPtr::ReleaseAndGetAddressOf

Libère l’interface associée à cet `ComPtr` , puis récupère l’adresse de la [ptr_](#ptr) membre de données, qui contient un pointeur vers l’interface qui a été publiée.

```cpp
T** ReleaseAndGetAddressOf();
```

### <a name="return-value"></a>Valeur de retour

L’adresse de la [ptr_](#ptr) membre de données de ce `ComPtr`.

## <a name="reset"></a>ComPtr::Reset

Libère toutes les références pour le pointeur vers l’interface qui est associé à ce `ComPtr`.

```cpp
unsigned long Reset();
```

### <a name="return-value"></a>Valeur de retour

Nombre de références éventuellement publiées.

## <a name="swap"></a>ComPtr::Swap

Échange l’interface gérée par l’actuel `ComPtr` avec l’interface gérée par le `ComPtr`.

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

