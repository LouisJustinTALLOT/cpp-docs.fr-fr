---
description: 'En savoir plus sur : classe WeakRef'
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
ms.openlocfilehash: 9c1c3edf7589dfd08e0ebab5389d2ca108d8e73c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97339408"
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
|[WeakRef::~WeakRef, destructeur](#tilde-weakref)|Désinitialise l’instance actuelle de la `WeakRef` classe.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[WeakRef::As, méthode](#as)|Définit le `ComPtr` paramètre de pointeur spécifié pour représenter l’interface spécifiée.|
|[WeakRef::AsIID, méthode](#asiid)|Définit le `ComPtr` paramètre de pointeur spécifié pour représenter l’ID d’interface spécifié.|
|[WeakRef::CopyTo, méthode](#copyto)|Assigne un pointeur vers une interface, si disponible, à la variable pointeur spécifiée.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[WeakRef::operator&, opérateur](#operator-ampersand-operator)|Retourne un `ComPtrRef` objet qui représente l' `WeakRef` objet actuel.|

## <a name="remarks"></a>Notes

Un `WeakRef` objet gère une *référence forte*, qui est associée à un objet et peut être valide ou non valide. Appelez la `As()` `AsIID()` méthode ou pour obtenir une référence forte. Lorsque la référence forte est valide, elle peut accéder à l’objet associé. Lorsque la référence forte n’est pas valide ( **`nullptr`** ), l’objet associé est inaccessible.

Un `WeakRef` objet est généralement utilisé pour représenter un objet dont l’existence est contrôlée par un thread ou une application externe. Par exemple, construisez un `WeakRef` objet à partir d’une référence à un objet fichier. Pendant que le fichier est ouvert, la référence forte est valide, mais si le fichier est fermé, la référence forte devient non valide.

Notez qu’il existe un changement de comportement des méthodes [As](#as), [AsIID](#asiid) et [CopyTo](#copyto) dans le Kit de développement logiciel SDK Windows 10. Précédemment, après avoir appelé l’une de ces méthodes, vous pouviez vérifier que le `WeakRef` pour **`nullptr`** déterminer si une référence forte a été obtenue avec succès, comme dans le code suivant :

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

Le code ci-dessus ne fonctionne pas lorsque vous utilisez le Kit de développement logiciel SDK Windows 10 (ou version ultérieure). Au lieu de cela, vérifiez le pointeur qui a été passé pour **`nullptr`** .

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

## <a name="weakrefweakref-destructor"></a><a name="tilde-weakref"></a> WeakRef :: ~ WeakRef, destructeur

Désinitialise l’instance actuelle de la `WeakRef` classe.

```cpp
~WeakRef();
```

## <a name="weakrefas-method"></a><a name="as"></a> WeakRef :: As, méthode

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

*ptr*<br/>
Lorsque cette opération est terminée, objet qui représente le paramètre *U*.

### <a name="return-value"></a>Valeur renvoyée

- S_OK si cette opération a échoué ; Sinon, HRESULT qui indique la raison de l’échec de l’opération, et *ptr* a la valeur **`nullptr`** .

- S_OK si cette opération réussit, mais que l' `WeakRef` objet actuel a déjà été libéré. *Ptr* de paramètre a la valeur **`nullptr`** .

- S_OK si cette opération s’effectue correctement, mais que l' `WeakRef` objet actuel n’est pas dérivé du paramètre *U*. *Ptr* de paramètre a la valeur **`nullptr`** .

### <a name="remarks"></a>Notes

Une erreur est émise si le paramètre *U* est `IWeakReference` , ou n’est pas dérivé de `IInspectable` .

Le premier modèle est le formulaire que vous devez utiliser dans votre code. Le deuxième modèle est une spécialisation d’assistance interne qui prend en charge les fonctionnalités du langage C++ telles que le mot clé de déduction de type [auto](../../cpp/auto-cpp.md) .

À partir du kit de développement logiciel (SDK) Windows 10, cette méthode ne définit pas l' `WeakRef` instance sur **`nullptr`** si la référence faible n’a pas pu être obtenue. vous devez donc éviter le code de vérification des erreurs qui vérifie le `WeakRef` pour **`nullptr`** . Au lieu de cela, vérifiez *ptr* pour **`nullptr`** .

## <a name="weakrefasiid-method"></a><a name="asiid"></a> WeakRef :: Asiid,, méthode

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

*ptr*<br/>
Lorsque cette opération est terminée, objet qui représente le paramètre *riid*.

### <a name="return-value"></a>Valeur renvoyée

- S_OK si cette opération a échoué ; Sinon, HRESULT qui indique la raison de l’échec de l’opération, et *ptr* a la valeur **`nullptr`** .

- S_OK si cette opération réussit, mais que l' `WeakRef` objet actuel a déjà été libéré. *Ptr* de paramètre a la valeur **`nullptr`** .

- S_OK si cette opération s’effectue correctement, mais que l' `WeakRef` objet actuel n’est pas dérivé du paramètre *riid*. *Ptr* de paramètre a la valeur **`nullptr`** . (Pour plus d’informations, consultez la section Notes.)

### <a name="remarks"></a>Notes

Une erreur est émise si le paramètre *riid* n’est pas dérivé de `IInspectable` . Cette erreur remplace la valeur de retour.

Le premier modèle est le formulaire que vous devez utiliser dans votre code. Le deuxième modèle (non illustré ici, mais déclaré dans le fichier d’en-tête) est une spécialisation d’assistance interne qui prend en charge les fonctionnalités du langage C++ telles que le mot clé de déduction de type [auto](../../cpp/auto-cpp.md) .

À partir du kit de développement logiciel (SDK) Windows 10, cette méthode ne définit pas l' `WeakRef` instance sur **`nullptr`** si la référence faible n’a pas pu être obtenue. vous devez donc éviter le code de vérification des erreurs qui vérifie le `WeakRef` pour **`nullptr`** . Au lieu de cela, vérifiez *ptr* pour **`nullptr`** .

## <a name="weakrefcopyto-method"></a><a name="copyto"></a> WeakRef :: CopyTo, méthode

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
Pointeur d' `IInspectable` interface. Une erreur est émise si *U* n’est pas dérivé de `IInspectable` .

*riid*<br/>
ID d’interface. Une erreur est émise si *riid* n’est pas dérivé de `IWeakReference` .

*ptr*<br/>
Pointeur doublement indirect vers `IInspectable` ou `IWeakReference` .

### <a name="return-value"></a>Valeur renvoyée

S_OK en cas de succès. Sinon, valeur HRESULT qui décrit l’erreur. Pour plus d’informations, consultez la **section Notes**.

### <a name="remarks"></a>Notes

La valeur de retour S_OK signifie que cette opération a réussi, mais elle n’indique pas si la référence faible a été résolue en une référence forte. Si S_OK est retourné, vérifiez que le paramètre *p* est une référence forte ; autrement dit, le paramètre *p* n’est pas égal à **`nullptr`** .

À partir du kit de développement logiciel (SDK) Windows 10, cette méthode ne définit pas l' `WeakRef` instance sur **`nullptr`** si la référence faible n’a pas pu être obtenue. vous devez donc éviter le code de vérification des erreurs qui vérifie le `WeakRef` pour **`nullptr`** . Au lieu de cela, vérifiez *ptr* pour **`nullptr`** .

## <a name="weakrefoperatoramp-operator"></a><a name="operator-ampersand-operator"></a> WeakRef :: Operator, &amp; opérateur

Retourne un `ComPtrRef` objet qui représente l' `WeakRef` objet actuel.

```cpp
Details::ComPtrRef<WeakRef> operator&() throw()
```

### <a name="return-value"></a>Valeur renvoyée

`ComPtrRef`Objet qui représente l’objet actuel `WeakRef` .

### <a name="remarks"></a>Notes

Il s’agit d’un opérateur d’assistance interne qui n’est pas destiné à être utilisé dans votre code.

## <a name="weakrefweakref-constructor"></a><a name="weakref"></a> WeakRef :: WeakRef, constructeur

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

*ptr*<br/>
Pointeur, référence ou référence rvalue à un objet existant qui initialise l' `WeakRef` objet actuel.

### <a name="remarks"></a>Notes

Le premier constructeur initialise un objet vide `WeakRef` . Le deuxième constructeur initialise un `WeakRef` objet à partir d’un pointeur vers l' `IWeakReference` interface. Le troisième constructeur initialise un `WeakRef` objet à partir d’une référence à un `ComPtr<IWeakReference>` objet. Les quatrième et cinquième constructeurs initialisent un `WeakRef` objet à partir d’un autre `WeakRef` objet.
