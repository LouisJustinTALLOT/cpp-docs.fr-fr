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
ms.openlocfilehash: 89c09ede972f5bdd5da1dde810cad31733bdf338
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372638"
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
L’interface `ComPtr` que le représente.

*U*<br/>
Une classe à `ComPtr` laquelle le courant est un ami. (Le modèle qui utilise ce paramètre est protégé).

## <a name="remarks"></a>Notes

`ComPtr<>`déclare un type qui représente le pointeur d’interface sous-jacent. Utilisez `ComPtr<>` pour déclarer une variable, puis utilisez`->`l’opérateur d’accès aux membres de flèche ( ) pour accéder à une fonction de membre d’interface.

Pour plus d’informations sur les pointeurs intelligents, consultez la sous-section « COM Smart Pointers » du sujet [des pratiques de codage COM](/windows/win32/LearnWin32/com-coding-practices) dans la bibliothèque MSDN.

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

Nom            | Description
--------------- | ---------------------------------------------------------------
`InterfaceType` | Un synonyme pour le type spécifié par le paramètre du modèle *T.*

### <a name="public-constructors"></a>Constructeurs publics

Nom                             | Description
-------------------------------- | --------------------------------------------------------------------------------------------------------------------
[ComPtr::ComPtr](#comptr)        | Initialise une nouvelle instance de la classe `ComPtr`. Les surcharges fournissent des constructeurs par défaut, de copie, de déplacement et de conversion.
[ComPtr: :ComPtr](#tilde-comptr) | Désinitialise une instance `ComPtr`de .

### <a name="public-methods"></a>M&#233;thodes publiques

Nom                                                      | Description
--------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
[ComPtr::Comme](#as)                                         | Retourne `ComPtr` un objet qui représente l’interface identifiée par le paramètre de modèle spécifié.
[ComPtr::AsIID](#asiid)                                   | Renvoie `ComPtr` un objet qui représente l’interface identifiée par l’ID d’interface spécifié.
[ComPtr::AsWeak](#asweak)                                 | Récupère une référence faible à l’objet actif.
[ComPtr::Attach](#attach)                                 | Associe `ComPtr` cela au type d’interface spécifié par le paramètre de type modèle actuel.
[ComPtr::CopyTo](#copyto)                                 | Copie l’interface actuelle ou `ComPtr` spécifiée associée à ce pointeur de sortie spécifié.
[ComPtr::Detach](#detach)                                 | Dissocie `ComPtr` cela de l’interface qu’il représente.
[ComPtr::Get](#get)                                       | Récupère un pointeur à l’interface `ComPtr`qui est associée à ce .
[ComPtr::GetAddressOf](#getaddressof)                     | Récupère l’adresse du membre [de données ptr_,](#ptr) qui contient un `ComPtr`pointeur à l’interface représentée par ce .
[ComPtr::ReleaseAndGetAddressOf](#releaseandgetaddressof) | Libère l’interface `ComPtr` associée à cela et récupère ensuite l’adresse du membre des données [ptr_,](#ptr) qui contient un pointeur sur l’interface qui a été libérée.
[ComPtr::Reset](#reset)                                   | Libère toutes les références pour le pointeur `ComPtr`à l’interface qui est associée à cela .
[ComPtr::Swap](#swap)                                     | Échange l’interface gérée `ComPtr` par le courant `ComPtr`avec l’interface gérée par le spécifié .

### <a name="protected-methods"></a>Méthodes protégées

Nom                                        | Description
------------------------------------------- | --------------------------------------------------------------------------------
[ComPtr::InternalAddRef](#internaladdref)   | Incréments le nombre de références `ComPtr`de l’interface associée à cette .
[ComPtr::InternalRelease](#internalrelease) | Effectue une opération de version COM `ComPtr`sur l’interface associée à cette .

### <a name="public-operators"></a>Op&#233;rateurs publics

Nom                                                                                           | Description
---------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------
[ComPtr::opérateur&](#operator-ampersand)                                                       | Récupère l’adresse du `ComPtr`courant .
[ComPtr::opérateur->](#operator-arrow)                                                          | Récupère un pointeur vers le type spécifié par le paramètre de modèle actuel.
[ComPtr::opérateur](#operator-assign)                                                          | Attribue une valeur au `ComPtr`courant .
[ComPtr::opérateur](#operator-equality)                                                       | Indique si deux objets `ComPtr` sont égaux.
[ComPtr::opérateur!](#operator-inequality)                                                     | Indique si deux objets `ComPtr` ne sont pas égaux.
[ComPtr::opérateur Microsoft::WRL::Details::BoolType](#operator-microsoft-wrl-details-booltype) | Indique si a `ComPtr` gère ou non la durée de vie de l’objet d’une interface.

### <a name="protected-data-members"></a>Membres de données protégés

Nom                 | Description
-------------------- | ------------------------------------------------------------------------------------------
[ComPtr::ptr](#ptr) | Contient un pointeur à l’interface qui `ComPtr`est associée à, et géré par ce .

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`ComPtr`

## <a name="requirements"></a>Spécifications

**En-tête :** client.h

**Espace de noms :** Microsoft::WRL

## <a name="comptrcomptr"></a><a name="tilde-comptr"></a>ComPtr: :ComPtr

Désinitialise une instance `ComPtr`de .

```cpp
WRL_NOTHROW ~ComPtr();
```

## <a name="comptras"></a><a name="as"></a>ComPtr::Comme

Retourne `ComPtr` un objet qui représente l’interface identifiée par le paramètre de modèle spécifié.

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
L’interface à représenter par paramètre *p*.

*P*<br/>
Un `ComPtr` objet qui représente l’interface spécifiée par le paramètre *U*. Le *paramètre p* ne `ComPtr` doit pas se référer à l’objet actuel.

### <a name="remarks"></a>Notes

Le premier modèle est le formulaire que vous devez utiliser dans votre code. Le deuxième modèle est une spécialisation d’assistance interne qui prend en charge les fonctionnalités du langage C++ telles que le mot clé de déduction de type [auto](../../cpp/auto-cpp.md) .

### <a name="return-value"></a>Valeur de retour

S_OK si l'opération réussit. Sinon, une valeur HRESULT indique l'erreur.

## <a name="comptrasiid"></a><a name="asiid"></a>ComPtr::AsIID

Renvoie `ComPtr` un objet qui représente l’interface identifiée par l’ID d’interface spécifié.

```cpp
WRL_NOTHROW HRESULT AsIID(
   REFIID riid,
   _Out_ ComPtr<IUnknown>* p
) const;
```

### <a name="parameters"></a>Paramètres

*riid*<br/>
ID d’interface.

*P*<br/>
Si l’objet a une interface dont l’ID est *synonyme de riid*, un pointeur doublement indirect à l’interface spécifiée par le paramètre *riid;* autrement, un `IUnknown`pointeur à .

### <a name="return-value"></a>Valeur de retour

S_OK si l'opération réussit. Sinon, une valeur HRESULT indique l'erreur.

## <a name="comptrasweak"></a><a name="asweak"></a>ComPtr::AsWeak

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

## <a name="comptrattach"></a><a name="attach"></a>ComPtr::Attach

Associe `ComPtr` cela au type d’interface spécifié par le paramètre de type modèle actuel.

```cpp
void Attach(
   _In_opt_ InterfaceType* other
);
```

### <a name="parameters"></a>Paramètres

*Autres*<br/>
Un type d’interface.

## <a name="comptrcomptr"></a><a name="comptr"></a>ComPtr::ComPtr

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
Le type de *l’autre* paramètre.

*Autres*<br/>
Un objet de type *U*.

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

Le premier constructeur est le constructeur par défaut, qui crée impliceusement un objet vide. Le deuxième constructeur spécifie [__nullptr](../../extensions/nullptr-cpp-component-extensions.md), qui crée explicitement un objet vide.

Le troisième constructeur crée un objet à partir de l’objet spécifié par un pointeur. Le ComPtr possède maintenant la mémoire pointue et y maintient un décompte de référence.

Les quatrième et cinquième constructeurs sont des constructeurs de copie. Le cinquième constructeur copie un objet s’il est convertible au type actuel.

Les sixième et septième constructeurs sont des constructeurs de déménagement. Le septième constructeur déplace un objet s’il est convertible au type actuel.

## <a name="comptrcopyto"></a><a name="copyto"></a>ComPtr::CopyTo

Copie l’interface actuelle ou `ComPtr` spécifiée associée à ce pointeur spécifié.

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

*Ptr*<br/>
Lorsque cette opération se termine, un pointeur à l’interface demandée.

*riid*<br/>
ID d’interface.

### <a name="return-value"></a>Valeur de retour

S_OK en cas de succès; autrement, un HRESULT qui `QueryInterface` indique pourquoi l’opération implicite a échoué.

### <a name="remarks"></a>Notes

La première fonction renvoie une copie d’un pointeur à l’interface associée à cette `ComPtr`. Cette fonction revient toujours S_OK.

La deuxième fonction `QueryInterface` effectue une opération sur `ComPtr` l’interface associée à celle-ci pour l’interface spécifiée par le paramètre *riid.*

La troisième fonction `QueryInterface` effectue une opération sur `ComPtr` l’interface associée à celle-ci pour l’interface sous-jacente du paramètre *U.*

## <a name="comptrdetach"></a><a name="detach"></a>ComPtr::Detach

Dissocie `ComPtr` cet objet de l’interface qu’il représente.

```cpp
T* Detach();
```

### <a name="return-value"></a>Valeur de retour

Un pointeur à l’interface `ComPtr` qui était représentée par cet objet.

## <a name="comptrget"></a><a name="get"></a>ComPtr::Get

Récupère un pointeur à l’interface `ComPtr`qui est associée à ce .

```cpp
T* Get() const;
```

### <a name="return-value"></a>Valeur de retour

Pointeur à l’interface `ComPtr`qui est associée à cela .

## <a name="comptrgetaddressof"></a><a name="getaddressof"></a>ComPtr::GetAddressOf

Récupère l’adresse du membre [de données ptr_,](#ptr) qui contient un `ComPtr`pointeur à l’interface représentée par ce .

```cpp
T* const* GetAddressOf() const;
T** GetAddressOf();
```

### <a name="return-value"></a>Valeur de retour

L’adresse d’une variable.

## <a name="comptrinternaladdref"></a><a name="internaladdref"></a>ComPtr::InternalAddRef

Incréments le nombre de références `ComPtr`de l’interface associée à cette .

```cpp
void InternalAddRef() const;
```

### <a name="remarks"></a>Notes

Cette méthode est protégée.

## <a name="comptrinternalrelease"></a><a name="internalrelease"></a>ComPtr::InternalRelease

Effectue une opération de version COM `ComPtr`sur l’interface associée à cette .

```cpp
void InternalRelease();
```

### <a name="remarks"></a>Notes

Cette méthode est protégée.

## <a name="comptroperatoramp"></a><a name="operator-ampersand"></a>ComPtr::opérateur&amp;

Libère l’interface `ComPtr` associée à cet objet, `ComPtr` puis récupère l’adresse de l’objet.

```cpp
Details::ComPtrRef<WeakRef> operator&()

const Details::ComPtrRef<const WeakRef> operator&() const
```

### <a name="return-value"></a>Valeur de retour

Une faible référence `ComPtr`au courant .

### <a name="remarks"></a>Notes

Cette méthode diffère de [ComPtr::GetAddressOf](#getaddressof) en ce que cette méthode libère une référence au pointeur d’interface. Utilisez `ComPtr::GetAddressOf` lorsque vous avez besoin de l’adresse du pointeur d’interface, mais ne voulez pas libérer cette interface.

## <a name="comptroperator-gt"></a><a name="operator-arrow"></a>ComPtr::opérateur-&gt;

Récupère un pointeur vers le type spécifié par le paramètre de modèle actuel.

```cpp
WRL_NOTHROW Microsoft::WRL::Details::RemoveIUnknown<InterfaceType>* operator->() const;
```

### <a name="return-value"></a>Valeur de retour

Pointeur sur le type spécifié par le nom de type modèle actuel.

### <a name="remarks"></a>Notes

Cette fonction d’aide élimine les frais généraux inutiles causés par l’utilisation de la macro STDMETHOD. Cette fonction `IUnknown` `private` fait `virtual`des types au lieu de .

## <a name="comptroperator"></a><a name="operator-assign"></a>ComPtr::opérateur

Attribue une valeur au `ComPtr`courant .

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
Un cours.

*Autres*<br/>
Une référence pointeur, référence ou rvalue `ComPtr`à un type ou à un autre.

### <a name="return-value"></a>Valeur de retour

Une référence au `ComPtr`courant .

### <a name="remarks"></a>Notes

La première version de cet opérateur attribue `ComPtr`une valeur vide au courant .

Dans la deuxième version, si le pointeur d’interface d’attribution n’est pas le même que le pointeur d’interface actuel, `ComPtr` le deuxième pointeur d’interface est attribué au courant `ComPtr`.

Dans la troisième version, le pointeur d’interface d’attribution est attribué au courant `ComPtr`.

Dans la quatrième version, si le pointeur d’interface de `ComPtr` la valeur d’attribution n’est `ComPtr`pas le même que le pointeur d’interface actuel, le deuxième pointeur d’interface est attribué au courant .

La cinquième version est un opérateur de copie; une référence `ComPtr` à un est `ComPtr`attribuée au courant .

La sixième version est un opérateur de copie qui utilise la sémantique de mouvement ; une référence rvalue `ComPtr` à un type s’il y `ComPtr`a un type statique et ensuite assignée au courant .

La septième version est un opérateur de copie qui utilise la sémantique de mouvement; une référence rvalue `ComPtr` à un type *U* est moulé `ComPtr`statique alors et attribué au courant .

## <a name="comptroperator"></a><a name="operator-equality"></a>ComPtr::opérateur

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

*Un*<br/>
Référence à un objet `ComPtr`.

*B*<br/>
Une référence `ComPtr` à un autre objet.

### <a name="return-value"></a>Valeur de retour

Le premier `true` opérateur cède si *l’objet a* est égal à l’objet *b*; autrement, `false`.

Les deuxième et `true` troisième opérateurs cèdent `nullptr`si *l’objet a* est égal à ; autrement, `false`.

## <a name="comptroperator"></a><a name="operator-inequality"></a>ComPtr::opérateur!

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

*Un*<br/>
Référence à un objet `ComPtr`.

*B*<br/>
Une référence `ComPtr` à un autre objet.

### <a name="return-value"></a>Valeur de retour

Le premier `true` opérateur cède si *l’objet a* n’est pas égal à l’objet *b*; autrement, `false`.

Les deuxième et `true` troisième opérateurs cèdent `nullptr`si l’objet *a* n’est pas égal à ; autrement, `false`.

## <a name="comptroperator-microsoftwrldetailsbooltype"></a><a name="operator-microsoft-wrl-details-booltype"></a>ComPtr::opérateur Microsoft::WRL::Details::BoolType

Indique si a `ComPtr` gère ou non la durée de vie de l’objet d’une interface.

```cpp
WRL_NOTHROW operator Microsoft::WRL::Details::BoolType() const;
```

### <a name="return-value"></a>Valeur de retour

Si une interface est `ComPtr`associée à cela, l’adresse du [BoolStruct : : Membre des](boolstruct-structure.md#member) données du membre ; autrement, `nullptr`.

## <a name="comptrptr_"></a><a name="ptr"></a>ComPtr::ptr

Contient un pointeur à l’interface qui `ComPtr`est associée à, et géré par ce .

```cpp
InterfaceType *ptr_;
```

### <a name="remarks"></a>Notes

`ptr_`est un membre interne et protégé des données.

## <a name="comptrreleaseandgetaddressof"></a><a name="releaseandgetaddressof"></a>ComPtr::ReleaseAndGetAddressOf

Libère l’interface `ComPtr` associée à cela et récupère ensuite l’adresse du membre des données [ptr_,](#ptr) qui contient un pointeur sur l’interface qui a été libérée.

```cpp
T** ReleaseAndGetAddressOf();
```

### <a name="return-value"></a>Valeur de retour

L’adresse du [ptr_](#ptr) membre des `ComPtr`données de cette .

## <a name="comptrreset"></a><a name="reset"></a>ComPtr::Reset

Libère toutes les références pour le pointeur `ComPtr`à l’interface qui est associée à cela .

```cpp
unsigned long Reset();
```

### <a name="return-value"></a>Valeur de retour

Nombre de références éventuellement publiées.

## <a name="comptrswap"></a><a name="swap"></a>ComPtr::Swap

Échange l’interface gérée `ComPtr` par le courant `ComPtr`avec l’interface gérée par le spécifié .

```cpp
void Swap(
   _Inout_ ComPtr&& r
);

void Swap(
   _Inout_ ComPtr& r
);
```

### <a name="parameters"></a>Paramètres

*R*<br/>
`ComPtr`.
