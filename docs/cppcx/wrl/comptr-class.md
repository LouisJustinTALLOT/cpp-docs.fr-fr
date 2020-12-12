---
description: 'En savoir plus sur : classe ComPtr'
title: ComPtr (classe)
ms.date: 06/02/2020
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
ms.openlocfilehash: a78264a0728382bf78b14193d130b19b0095240b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97273174"
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

`ComPtr<>` déclare un type qui représente le pointeur d’interface sous-jacent. Utilisez `ComPtr<>` pour déclarer une variable, puis utilisez l’opérateur d’accès aux membres Arrow ( `->` ) pour accéder à une fonction membre d’interface.

Pour plus d’informations sur les pointeurs intelligents, consultez la sous-section « pointeurs intelligents COM » de l’article [pratiques de codage com](/windows/win32/LearnWin32/com-coding-practices) .

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

Nom            | Description
--------------- | ---------------------------------------------------------------
`InterfaceType` | Synonyme du type spécifié par le paramètre de modèle *T* .

### <a name="public-constructors"></a>Constructeurs publics

Nom                             | Description
-------------------------------- | --------------------------------------------------------------------------------------------------------------------
[ComPtr :: ComPtr](#comptr)        | Initialise une nouvelle instance de la classe `ComPtr`. Les surcharges fournissent des constructeurs par défaut, de copie, de déplacement et de conversion.
[ComPtr :: ~ ComPtr](#tilde-comptr) | Déinitialise une instance de `ComPtr` .

### <a name="public-methods"></a>M&#233;thodes publiques

Nom                                                      | Description
--------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
[ComPtr :: As](#as)                                         | Retourne un `ComPtr` objet qui représente l’interface identifiée par le paramètre de modèle spécifié.
[ComPtr :: Asiid,](#asiid)                                   | Retourne un `ComPtr` objet qui représente l’interface identifiée par l’ID d’interface spécifié.
[ComPtr :: Asweak,](#asweak)                                 | Récupère une référence faible à l’objet actif.
[ComPtr :: Attach](#attach)                                 | Associe ce au `ComPtr` type d’interface spécifié par le paramètre de type de modèle actuel.
[ComPtr :: CopyTo](#copyto)                                 | Copie l’interface actuelle ou spécifiée associée à ce `ComPtr` vers le pointeur de sortie spécifié.
[ComPtr ::D Etach](#detach)                                 | Dissocie ce `ComPtr` de l’interface qu’il représente.
[ComPtr :: obtient](#get)                                       | Récupère un pointeur vers l’interface associée à ce `ComPtr` .
[ComPtr :: Getaddressof,](#getaddressof)                     | Récupère l’adresse du membre de données [PTR_](#ptr) , qui contient un pointeur vers l’interface représentée par ce `ComPtr` .
[ComPtr :: Releaseandgetaddressof,](#releaseandgetaddressof) | Libère l’interface associée à ce, puis `ComPtr` récupère l’adresse du membre de données [PTR_](#ptr) , qui contient un pointeur vers l’interface qui a été libérée.
[ComPtr::Reset](#reset)                                   | Libère l’interface associée à ce `ComPtr` et retourne le nouveau décompte de références.
[ComPtr :: swap](#swap)                                     | Échange l’interface gérée par le actuel `ComPtr` avec l’interface gérée par le spécifié `ComPtr` .

### <a name="protected-methods"></a>Méthodes protégées

Nom                                        | Description
------------------------------------------- | --------------------------------------------------------------------------------
[ComPtr :: Internaladdref,](#internaladdref)   | Incrémente le décompte de références de l’interface associée à ce `ComPtr` .
[ComPtr :: InternalRelease,](#internalrelease) | Exécute une opération de mise en service COM sur l’interface associée à ce `ComPtr` .

### <a name="public-operators"></a>Op&#233;rateurs publics

Nom                                                                                           | Description
---------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------
[ComPtr :: Operator&](#operator-ampersand)                                                       | Récupère l’adresse du actuel `ComPtr` .
[ComPtr :: Operator->](#operator-arrow)                                                          | Récupère un pointeur vers le type spécifié par le paramètre de modèle actuel.
[ComPtr :: Operator =](#operator-assign)                                                          | Assigne une valeur à l’objet actuel `ComPtr` .
[ComPtr :: Operator = =](#operator-equality)                                                       | Indique si deux objets `ComPtr` sont égaux.
[ComPtr :: Operator ! =](#operator-inequality)                                                     | Indique si deux `ComPtr` objets ne sont pas égaux.
[ComPtr :: Operator Microsoft :: WRL ::D étails :: Booltype,](#operator-microsoft-wrl-details-booltype) | Indique si un `ComPtr` gère la durée de vie des objets d’une interface.

### <a name="protected-data-members"></a>Membres de données protégés

Nom                 | Description
-------------------- | ------------------------------------------------------------------------------------------
[ComPtr ::p tr_](#ptr) | Contient un pointeur vers l’interface qui est associée à et gérée par ce `ComPtr` .

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`ComPtr`

## <a name="requirements"></a>Spécifications

**En-tête :** client.h

**Espace de noms :** Microsoft::WRL

## <a name="comptrcomptr"></a><a name="tilde-comptr"></a> ComPtr :: ~ ComPtr

Déinitialise une instance de `ComPtr` .

```cpp
WRL_NOTHROW ~ComPtr();
```

## <a name="comptras"></a><a name="as"></a> ComPtr :: As

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
`ComPtr`Objet qui représente l’interface spécifiée par le paramètre *U*. Le paramètre *p* ne doit pas faire référence à l' `ComPtr` objet actuel.

### <a name="remarks"></a>Notes

Le premier modèle est le formulaire que vous devez utiliser dans votre code. Le deuxième modèle est une spécialisation d’assistance interne. Il prend en charge les fonctionnalités du langage C++ telles que le mot clé de déduction de type [auto](../../cpp/auto-cpp.md) .

### <a name="return-value"></a>Valeur renvoyée

S_OK si l'opération réussit. Sinon, une valeur HRESULT indique l'erreur.

## <a name="comptrasiid"></a><a name="asiid"></a> ComPtr :: Asiid,

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
Si l’objet a une interface dont l’ID est égal à *riid*, pointeur doublement indirect vers l’interface spécifiée par le paramètre *riid* . Sinon, pointeur vers `IUnknown` .

### <a name="return-value"></a>Valeur renvoyée

S_OK si l'opération réussit. Sinon, une valeur HRESULT indique l'erreur.

## <a name="comptrasweak"></a><a name="asweak"></a> ComPtr :: Asweak,

Récupère une référence faible à l’objet actif.

```cpp
HRESULT AsWeak(
   _Out_ WeakRef* pWeakRef
);
```

### <a name="parameters"></a>Paramètres

*pWeakRef*<br/>
Lorsque cette opération est terminée, pointeur vers un objet de référence faible.

### <a name="return-value"></a>Valeur renvoyée

S_OK si l'opération réussit. Sinon, une valeur HRESULT indique l'erreur.

## <a name="comptrattach"></a><a name="attach"></a> ComPtr :: Attach

Associe ce au `ComPtr` type d’interface spécifié par le paramètre de type de modèle actuel.

```cpp
void Attach(
   _In_opt_ InterfaceType* other
);
```

### <a name="parameters"></a>Paramètres

*autres*<br/>
Type d’interface.

## <a name="comptrcomptr"></a><a name="comptr"></a> ComPtr :: ComPtr

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

*autres*<br/>
Objet de type *U*.

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

Le premier constructeur est le constructeur par défaut, qui crée implicitement un objet vide. Le deuxième constructeur spécifie [__nullptr](../../extensions/nullptr-cpp-component-extensions.md), qui crée explicitement un objet vide.

Le troisième constructeur crée un objet à partir de l’objet spécifié par un pointeur. Le ComPtr est maintenant propriétaire de la mémoire pointée et gère un décompte de références.

Les quatrième et cinquième constructeurs sont des constructeurs de copie. Le cinquième constructeur copie un objet s’il est convertible en type actuel.

Les sixième et septième constructeurs sont des constructeurs de déplacement. Le septième constructeur déplace un objet s’il est convertible en type actuel.

## <a name="comptrcopyto"></a><a name="copyto"></a> ComPtr :: CopyTo

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

### <a name="return-value"></a>Valeur renvoyée

S_OK en cas de réussite ; Sinon, HRESULT qui indique la raison de l’échec de l’opération implicite `QueryInterface` .

### <a name="remarks"></a>Notes

La première fonction retourne une copie d’un pointeur vers l’interface associée à ce `ComPtr` . Cette fonction retourne toujours S_OK.

La deuxième fonction effectue une `QueryInterface` opération sur l’interface associée à ce `ComPtr` pour l’interface spécifiée par le paramètre *riid* .

La troisième fonction effectue une `QueryInterface` opération sur l’interface associée à ce `ComPtr` pour l’interface sous-jacente du paramètre  *U* .

## <a name="comptrdetach"></a><a name="detach"></a> ComPtr ::D Etach

Dissocie cet `ComPtr` objet de l’interface qu’il représente.

```cpp
T* Detach();
```

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers l’interface qui a été représentée par cet `ComPtr` objet.

## <a name="comptrget"></a><a name="get"></a> ComPtr :: obtient

Récupère un pointeur vers l’interface associée à ce `ComPtr` .

```cpp
T* Get() const;
```

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers l’interface associée à ce `ComPtr` .

## <a name="comptrgetaddressof"></a><a name="getaddressof"></a> ComPtr :: Getaddressof,

Récupère l’adresse du membre de données [PTR_](#ptr) , qui contient un pointeur vers l’interface représentée par ce `ComPtr` .

```cpp
T* const* GetAddressOf() const;
T** GetAddressOf();
```

### <a name="return-value"></a>Valeur renvoyée

Adresse d’une variable.

## <a name="comptrinternaladdref"></a><a name="internaladdref"></a> ComPtr :: Internaladdref,

Incrémente le décompte de références de l’interface associée à ce `ComPtr` .

```cpp
void InternalAddRef() const;
```

### <a name="remarks"></a>Notes

Cette méthode est protégée.

## <a name="comptrinternalrelease"></a><a name="internalrelease"></a> ComPtr :: InternalRelease,

Exécute une opération de mise en service COM sur l’interface associée à ce `ComPtr` .

```cpp
unsigned long InternalRelease();
```

### <a name="remarks"></a>Notes

Cette méthode est protégée.

## <a name="comptroperatoramp"></a><a name="operator-ampersand"></a> ComPtr ::, opérateur&amp;

Libère l’interface associée à cet `ComPtr` objet, puis récupère l’adresse de l' `ComPtr` objet.

```cpp
Details::ComPtrRef<WeakRef> operator&()

const Details::ComPtrRef<const WeakRef> operator&() const
```

### <a name="return-value"></a>Valeur renvoyée

Référence faible à l’objet actuel `ComPtr` .

### <a name="remarks"></a>Notes

Cette méthode diffère de [ComPtr :: getaddressof,](#getaddressof) dans le fait que cette méthode libère une référence au pointeur d’interface. Utilisez `ComPtr::GetAddressOf` lorsque vous avez besoin de l’adresse du pointeur d’interface, mais que vous ne souhaitez pas libérer cette interface.

## <a name="comptroperator-gt"></a><a name="operator-arrow"></a> ComPtr :: Operator-&gt;

Récupère un pointeur vers le type spécifié par le paramètre de modèle actuel.

```cpp
WRL_NOTHROW Microsoft::WRL::Details::RemoveIUnknown<InterfaceType>* operator->() const;
```

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers le type spécifié par le nom du type de modèle actuel.

### <a name="remarks"></a>Notes

Cette fonction d’assistance supprime la surcharge inutile provoquée par l’utilisation de la macro STDMETHOD. Cette fonction effectue `IUnknown` **`private`** des types au lieu de **`virtual`** .

## <a name="comptroperator"></a><a name="operator-assign"></a> ComPtr :: Operator =

Assigne une valeur à l’objet actuel `ComPtr` .

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

*autres*<br/>
Une référence de pointeur, de référence ou rvalue à un type ou un autre `ComPtr` .

### <a name="return-value"></a>Valeur renvoyée

Référence à l’objet actuel `ComPtr` .

### <a name="remarks"></a>Notes

La première version de cet opérateur assigne une valeur vide à l’objet actuel `ComPtr` .

Dans la deuxième version, si le pointeur d’interface Assigning n’est pas le même que le `ComPtr` pointeur d’interface actuel, le deuxième pointeur d’interface est assigné à l’objet actuel `ComPtr` .

Dans la troisième version, le pointeur d’interface Assigning est assigné à l’objet actuel `ComPtr` .

Dans la quatrième version, si le pointeur d’interface de la valeur d’assignation n’est pas le même que le `ComPtr` pointeur d’interface actuel, le deuxième pointeur d’interface est assigné à l’objet actuel `ComPtr` .

La cinquième version est un opérateur de copie ; une référence à un `ComPtr` est assignée à l’objet actuel `ComPtr` .

La sixième version est un opérateur de copie qui utilise la sémantique de déplacement. Référence rvalue à un `ComPtr` si tout type est Cast statique, puis assigné à l’objet actuel `ComPtr` .

La septième version est un opérateur de copie qui utilise la sémantique de déplacement. une référence rvalue à un `ComPtr` de type *U* est un cast statique, puis assigné à l’objet actuel `ComPtr` .

## <a name="comptroperator"></a><a name="operator-equality"></a> ComPtr :: Operator = =

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

*un*<br/>
Référence à un objet `ComPtr`.

*b*<br/>
Référence à un autre `ComPtr` objet.

### <a name="return-value"></a>Valeur renvoyée

Le premier opérateur produit **`true`** si l’objet *a* est égal à l’objet *b*; sinon, **`false`** .

Le deuxième et le troisième opérateur produisent **`true`** si l’objet *a* est égal à **`nullptr`** ; sinon, **`false`** .

## <a name="comptroperator"></a><a name="operator-inequality"></a> ComPtr :: Operator ! =

Indique si deux `ComPtr` objets ne sont pas égaux.

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

*un*<br/>
Référence à un objet `ComPtr`.

*b*<br/>
Référence à un autre `ComPtr` objet.

### <a name="return-value"></a>Valeur renvoyée

Le premier opérateur produit **`true`** si l’objet *a* n’est pas égal à l’objet *b*; sinon, **`false`** .

Le deuxième et le troisième opérateur produisent **`true`** si l’objet *a* n’est pas égal à **`nullptr`** ; sinon, **`false`** .

## <a name="comptroperator-microsoftwrldetailsbooltype"></a><a name="operator-microsoft-wrl-details-booltype"></a> ComPtr :: Operator Microsoft :: WRL ::D étails :: Booltype,

Indique si un `ComPtr` gère la durée de vie des objets d’une interface.

```cpp
WRL_NOTHROW operator Microsoft::WRL::Details::BoolType() const;
```

### <a name="return-value"></a>Valeur renvoyée

Si une interface est associée à, il s’agit `ComPtr` de l’adresse du membre de données [BoolStruct :: Member](boolstruct-structure.md#member) ; sinon, **`nullptr`** .

## <a name="comptrptr_"></a><a name="ptr"></a> ComPtr ::p tr_

Contient un pointeur vers l’interface qui est associée à et gérée par ce `ComPtr` .

```cpp
InterfaceType *ptr_;
```

### <a name="remarks"></a>Notes

`ptr_` est un membre de données interne et protégé.

## <a name="comptrreleaseandgetaddressof"></a><a name="releaseandgetaddressof"></a> ComPtr :: Releaseandgetaddressof,

Libère l’interface associée à ce, puis `ComPtr` récupère l’adresse du membre de données [PTR_](#ptr) , qui contient un pointeur vers l’interface qui a été libérée.

```cpp
T** ReleaseAndGetAddressOf();
```

### <a name="return-value"></a>Valeur renvoyée

Adresse du membre de données de [PTR_](#ptr) de ce `ComPtr` .

## <a name="comptrreset"></a><a name="reset"></a> ComPtr :: Reset

Libère l’interface associée à ce `ComPtr` et retourne le nouveau décompte de références.

```cpp
unsigned long Reset();
```

### <a name="return-value"></a>Valeur renvoyée

Nombre de références restantes à l’interface sous-jacente, le cas échéant.

## <a name="comptrswap"></a><a name="swap"></a> ComPtr :: swap

Échange l’interface gérée par le actuel `ComPtr` avec l’interface gérée par le spécifié `ComPtr` .

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
