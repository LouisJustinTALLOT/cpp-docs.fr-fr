---
title: WeakRef, classe
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::WeakRef
- client/Microsoft::WRL::WeakRef::~WeakRef
- client/Microsoft::WRL::WeakRef::As
- client/Microsoft::WRL::WeakRef::AsIID
- client/Microsoft::WRL::WeakRef::CopyTo
- client/Microsoft::WRL::WeakRef::operator&
- client/Microsoft::WRL::WeakRef::WeakRef
helpviewer_keywords:
- Microsoft::WRL::WeakRef class
- Microsoft::WRL::WeakRef::~WeakRef, destructor
- Microsoft::WRL::WeakRef::As method
- Microsoft::WRL::WeakRef::AsIID method
- Microsoft::WRL::WeakRef::CopyTo method
- Microsoft::WRL::WeakRef::operator& operator
- Microsoft::WRL::WeakRef::WeakRef, constructor
ms.assetid: 572be703-c641-496c-8af5-ad6164670ba1
ms.openlocfilehash: 681f5a64c3e2902c66facbd4f0ac3a3663a7e79d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374256"
---
# <a name="weakref-class"></a>WeakRef, classe

Représente une *référence faible* qui peut être utilisée uniquement par le Windows Runtime, pas par le COM classique. Une référence faible représente un objet qui peut être accessible ou non.

## <a name="syntax"></a>Syntaxe

```cpp
class WeakRef : public ComPtr<IWeakReference>;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[WeakRef::WeakRef, constructeur](#weakref)|Initialise une nouvelle instance de la classe `WeakRef`.|
|[WeakRef::~WeakRef, destructeur](#tilde-weakref)|Désinitialise l’instance actuelle `WeakRef` de la classe.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[WeakRef::As, méthode](#as)|Définit le `ComPtr` paramètre de pointeur spécifié pour représenter l’interface spécifiée.|
|[WeakRef::AsIID, méthode](#asiid)|Définit le `ComPtr` paramètre de pointeur spécifié pour représenter l’ID d’interface spécifié.|
|[WeakRef::CopyTo, méthode](#copyto)|Assigne un pointeur vers une interface, si disponible, à la variable pointeur spécifiée.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[WeakRef::operator&, opérateur](#operator-ampersand-operator)|Retourne `ComPtrRef` un objet qui `WeakRef` représente l’objet actuel.|

## <a name="remarks"></a>Notes

Un `WeakRef` objet maintient une *référence forte,* qui est associée à un objet, et peut être valide ou invalide. Appelez `As()` la `AsIID()` méthode ou l’obtention d’une référence forte. Lorsque la référence forte est valide, elle peut accéder à l’objet associé. Lorsque la référence forte n’est pas valide (`nullptr`), l’objet associé n’est pas accessible.

Un `WeakRef` objet est généralement utilisé pour représenter un objet dont l’existence est contrôlée par un thread ou une application externe. Par exemple, `WeakRef` construisez un objet à partir d’une référence à un objet de fichier. Pendant que le fichier est ouvert, la référence forte est valide, mais si le fichier est fermé, la référence forte devient non valide.

Notez qu’il existe un changement de comportement des méthodes [As](#as), [AsIID](#asiid) et [CopyTo](#copyto) dans le Kit de développement logiciel SDK Windows 10. Auparavant, après avoir appelé l’une `WeakRef` de `nullptr` ces méthodes, vous pouvez vérifier la pour déterminer si une référence forte a été obtenue avec succès, comme dans le code suivant:

```cpp
WeakRef wr;
strongComptrRef.AsWeak(&wr);

// Now suppose that the object strongComPtrRef points to no longer exists
// and the following code tries to get a strong ref from the weak ref:
ComPtr<ISomeInterface> strongRef;
HRESULT hr = wr.As(&strongRef);

// This check won't work with the Windows 10 SDK version of the library.
// Check the input pointer instead.
if(wr == nullptr)
{
    wprintf(L"Couldn’t get strong ref!");
}
```

Le code ci-dessus ne fonctionne pas lorsque vous utilisez le Kit de développement logiciel SDK Windows 10 (ou version ultérieure). Au lieu de cela, vérifier `nullptr`le pointeur qui a été passé pour .

```cpp
if (strongRef == nullptr)
{
    wprintf(L"Couldn't get strong ref!");
}
```

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`ComPtr`

`WeakRef`

## <a name="requirements"></a>Spécifications

**En-tête :** client.h

**Espace de noms :** Microsoft::WRL

## <a name="weakrefweakref-destructor"></a><a name="tilde-weakref"></a>FaibleRef::-WeakRef Destructor

Désinitialise l’instance actuelle `WeakRef` de la classe.

```cpp
~WeakRef();
```

## <a name="weakrefas-method"></a><a name="as"></a>WeakRef::Comme méthode

Définit le `ComPtr` paramètre de pointeur spécifié pour représenter l’interface spécifiée.

```cpp
template<typename U>
HRESULT As(
   _Out_ ComPtr<U>* ptr
);

template<typename U>
HRESULT As(
   _Out_ Details::ComPtrRef<ComPtr<U>> ptr
);
```

### <a name="parameters"></a>Paramètres

*U*<br/>
ID d’interface.

*Ptr*<br/>
Lorsque cette opération se termine, un objet qui représente le paramètre *U*.

### <a name="return-value"></a>Valeur de retour

- S_OK si cette opération réussit; autrement, un HRESULT qui indique la raison pour laquelle `nullptr`l’opération a échoué, et *ptr* est réglé à .

- S_OK si cette opération réussit, mais `WeakRef` l’objet actuel a déjà été libéré. Paramètre *ptr* `nullptr`est réglé à .

- S_OK si cette opération réussit, `WeakRef` mais l’objet actuel n’est pas dérivé du paramètre *U*. Paramètre *ptr* `nullptr`est réglé à .

### <a name="remarks"></a>Notes

Une erreur est émise si `IWeakReference`le paramètre `IInspectable` *U* est, ou n’est pas dérivé de .

Le premier modèle est le formulaire que vous devez utiliser dans votre code. Le deuxième modèle est une spécialisation d’assistance interne qui prend en charge les fonctionnalités du langage C++ telles que le mot clé de déduction de type [auto](../../cpp/auto-cpp.md) .

À partir de la Windows 10 SDK, `WeakRef` `nullptr` cette méthode ne fixe pas l’instance à si la référence `WeakRef` `nullptr`faible n’a pas pu être obtenue, de sorte que vous devriez éviter le code de vérification des erreurs qui vérifie le pour . Au lieu de `nullptr`cela, vérifier *ptr* pour .

## <a name="weakrefasiid-method"></a><a name="asiid"></a>WeakRef::Méthode AsIID

Définit le `ComPtr` paramètre de pointeur spécifié pour représenter l’ID d’interface spécifié.

```cpp
HRESULT AsIID(
   REFIID riid,
   _Out_ ComPtr<IInspectable>* ptr
);
```

### <a name="parameters"></a>Paramètres

*riid*<br/>
ID d’interface.

*Ptr*<br/>
Lorsque cette opération se termine, un objet qui représente *le paramètre riide*.

### <a name="return-value"></a>Valeur de retour

- S_OK si cette opération réussit; autrement, un HRESULT qui indique la raison pour laquelle `nullptr`l’opération a échoué, et *ptr* est réglé à .

- S_OK si cette opération réussit, mais `WeakRef` l’objet actuel a déjà été libéré. Paramètre *ptr* `nullptr`est réglé à .

- S_OK si cette opération réussit, mais `WeakRef` l’objet actuel n’est pas dérivé du *paramètre riid*. Paramètre *ptr* `nullptr`est réglé à . (Pour plus d’informations, consultez la section Notes.)

### <a name="remarks"></a>Notes

Une erreur est émise si *le paramètre riid* n’est pas dérivé de `IInspectable`. Cette erreur remplace la valeur de retour.

Le premier modèle est le formulaire que vous devez utiliser dans votre code. Le deuxième modèle (non illustré ici, mais déclaré dans le fichier d’en-tête) est une spécialisation d’assistance interne qui prend en charge les fonctionnalités du langage C++ telles que le mot clé de déduction de type [auto](../../cpp/auto-cpp.md) .

À partir de la Windows 10 SDK, `WeakRef` `nullptr` cette méthode ne fixe pas l’instance à si la référence `WeakRef` `nullptr`faible n’a pas pu être obtenue, de sorte que vous devriez éviter le code de vérification des erreurs qui vérifie le pour . Au lieu de `nullptr`cela, vérifier *ptr* pour .

## <a name="weakrefcopyto-method"></a><a name="copyto"></a>WeakRef::CopyTo Méthode

Assigne un pointeur vers une interface, si disponible, à la variable pointeur spécifiée.

```cpp
HRESULT CopyTo(
   REFIID riid,
   _Deref_out_ IInspectable** ptr
);

template<typename U>
HRESULT CopyTo(
   _Deref_out_ U** ptr
);

HRESULT CopyTo(
   _Deref_out_ IWeakReference** ptr
);
```

### <a name="parameters"></a>Paramètres

*U*<br/>
Pointeur `IInspectable` d’une interface. Une erreur est *U* émise si U `IInspectable`n’est pas dérivé de .

*riid*<br/>
ID d’interface. Une erreur est émise si la `IWeakReference` *riid n’est* pas dérivée de .

*Ptr*<br/>
Un pointeur doublement `IInspectable` `IWeakReference`indirect à ou .

### <a name="return-value"></a>Valeur de retour

S_OK en cas de succès. Sinon, valeur HRESULT qui décrit l’erreur. Pour plus d’informations, voir **Remarques**.

### <a name="remarks"></a>Notes

La valeur de retour S_OK signifie que cette opération a réussi, mais elle n’indique pas si la référence faible a été résolue en une référence forte. Si S_OK est retournée, testez ce paramètre *p* est une référence forte; c’est-à-dire, le `nullptr`paramètre *p* n’est pas égal à .

À partir de la Windows 10 SDK, `WeakRef` `nullptr` cette méthode ne fixe pas l’instance à si la `WeakRef` référence `nullptr`faible n’a pas pu être obtenue, de sorte que vous devriez éviter le code de vérification des erreurs qui vérifie le pour . Au lieu de `nullptr`cela, vérifier *ptr* pour .

## <a name="weakrefoperatoramp-operator"></a><a name="operator-ampersand-operator"></a>WeakRef::opérateur&amp; opérateur

Retourne `ComPtrRef` un objet qui `WeakRef` représente l’objet actuel.

```cpp
Details::ComPtrRef<WeakRef> operator&() throw()
```

### <a name="return-value"></a>Valeur de retour

Un `ComPtrRef` objet qui `WeakRef` représente l’objet actuel.

### <a name="remarks"></a>Notes

Il s’agit d’un opérateur d’aide interne qui n’est pas destiné à être utilisé dans votre code.

## <a name="weakrefweakref-constructor"></a><a name="weakref"></a>WeakRef::WeakRef Constructor

Initialise une nouvelle instance de la classe `WeakRef`.

```cpp
WeakRef();
WeakRef(
   decltype(__nullptr)
);

WeakRef(
   _In_opt_ IWeakReference* ptr
);

WeakRef(
   const ComPtr<IWeakReference>& ptr
);

WeakRef(
   const WeakRef& ptr
);

WeakRef(
   _Inout_ WeakRef&& ptr
);
```

### <a name="parameters"></a>Paramètres

*Ptr*<br/>
Un pointeur, une référence ou une référence à un objet `WeakRef` existant qui initialise l’objet actuel.

### <a name="remarks"></a>Notes

Le premier constructeur initialise `WeakRef` un objet vide. Le deuxième constructeur initialise `WeakRef` un objet d’un pointeur à l’interface. `IWeakReference` Le troisième constructeur initialise `WeakRef` un objet à `ComPtr<IWeakReference>` partir d’une référence à un objet. Les quatrième et cinquième constructeurs `WeakRef` initialisent `WeakRef` un objet d’un autre objet.
