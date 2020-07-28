---
title: WeakReference, classe
ms.date: 09/24/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::WeakReference
- implements/Microsoft::WRL::Details::WeakReference::DecrementStrongReference
- implements/Microsoft::WRL::Details::WeakReference::IncrementStrongReference
- implements/Microsoft::WRL::Details::WeakReference::Resolve
- implements/Microsoft::WRL::Details::WeakReference::SetUnknown
- implements/Microsoft::WRL::Details::WeakReference::~WeakReference
- implements/Microsoft::WRL::Details::WeakReference::WeakReference
helpviewer_keywords:
- Microsoft::WRL::Details::WeakReference class
- Microsoft::WRL::Details::WeakReference::DecrementStrongReference method
- Microsoft::WRL::Details::WeakReference::IncrementStrongReference method
- Microsoft::WRL::Details::WeakReference::Resolve method
- Microsoft::WRL::Details::WeakReference::SetUnknown method
- Microsoft::WRL::Details::WeakReference::~WeakReference, destructor
- Microsoft::WRL::Details::WeakReference::WeakReference, constructor
ms.assetid: 3f4c956b-dbbd-49b1-8cfa-9509a9956c97
ms.openlocfilehash: 9a367a61a029abe1be599b1e262e279402149ccd
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220455"
---
# <a name="weakreference-class"></a>WeakReference, classe

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

## <a name="syntax"></a>Syntaxe

```cpp
class WeakReference;
```

## <a name="remarks"></a>Notes

Représente une *référence faible* qui peut être utilisée avec le Windows Runtime ou le com classique. Une référence faible représente un objet qui peut être accessible ou non.

Un `WeakReference` objet gère une *référence forte*, qui est un pointeur vers un objet, et un *nombre de références fort*, qui est le nombre de copies de la référence forte qui ont été distribuées par la `Resolve()` méthode. Alors que le nombre de références fortes est différent de zéro, la référence forte est valide et l’objet est accessible. Lorsque le nombre de références fortes est égal à zéro, la référence forte n’est pas valide et l’objet est inaccessible.

Un `WeakReference` objet est généralement utilisé pour représenter un objet dont l’existence est contrôlée par un thread ou une application externe. Par exemple, construisez un `WeakReference` objet à partir d’une référence à un objet fichier. Pendant que le fichier est ouvert, la référence forte est valide, mais si le fichier est fermé, la référence forte devient non valide.

Les `WeakReference` méthodes sont thread-safe.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

Nom                                                  | Description
----------------------------------------------------- | ---------------------------------------------------------------------------
[WeakReference :: WeakReference](#weakreference)        | Initialise une nouvelle instance de la classe `WeakReference`.
[WeakReference :: ~ WeakReference](#tilde-weakreference) | Déinitialise (détruit) l’instance actuelle de la `WeakReference` classe.

### <a name="public-methods"></a>M&#233;thodes publiques

Nom                                                                 | Description
-------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------
[WeakReference ::D ecrementStrongReference](#decrementstrongreference) | Décrémente le décompte de références fortes de l' `WeakReference` objet actuel.
[WeakReference :: Incrementstrongreference,](#incrementstrongreference) | Incrémente le décompte de références fortes de l' `WeakReference` objet actuel.
[WeakReference :: Resolve](#resolve)                                   | Définit le pointeur spécifié sur la valeur de référence forte actuelle si le nombre de références fortes est différent de zéro.
[WeakReference :: Setunknown,](#setunknown)                             | Définit la référence forte de l' `WeakReference` objet actuel sur le pointeur d’interface spécifié.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`WeakReference`

## <a name="requirements"></a>Spécifications

**En-tête :** Implements. h

**Espace de noms :** Microsoft :: WRL ::D étails

## <a name="weakreferenceweakreference"></a><a name="tilde-weakreference"></a>WeakReference :: ~ WeakReference

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

```cpp
virtual ~WeakReference();
```

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

Désinitialise l’instance actuelle de la `WeakReference` classe.

## <a name="weakreferencedecrementstrongreference"></a><a name="decrementstrongreference"></a>WeakReference ::D ecrementStrongReference

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

```cpp
ULONG DecrementStrongReference();
```

### <a name="remarks"></a>Notes

Décrémente le décompte de références fortes de l' `WeakReference` objet actuel.

Lorsque le nombre de références fortes est égal à zéro, la référence forte est définie sur **`nullptr`** .

### <a name="return-value"></a>Valeur de retour

Nombre de références fortes décrémenté.

## <a name="weakreferenceincrementstrongreference"></a><a name="incrementstrongreference"></a>WeakReference :: Incrementstrongreference,

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

```cpp
ULONG IncrementStrongReference();
```

### <a name="return-value"></a>Valeur de retour

Nombre de références fortes incrémentées.

### <a name="remarks"></a>Notes

Incrémente le décompte de références fortes de l' `WeakReference` objet actuel.

## <a name="weakreferenceresolve"></a><a name="resolve"></a>WeakReference :: Resolve

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

```cpp
STDMETHOD(Resolve)
   (REFIID riid,
   _Deref_out_opt_ IInspectable **ppvObject
);
```

### <a name="parameters"></a>Paramètres

*riid*<br/>
ID d’interface.

*ppvObject*<br/>
Lorsque cette opération est terminée, il s’agit d’une copie de la référence forte actuelle si le nombre de références fortes est différent de zéro.

### <a name="return-value"></a>Valeur de retour

- S_OK si cette opération réussit et si le nombre de références fortes est égal à zéro. Le paramètre *ppvObject* a la valeur **`nullptr`** .

- S_OK si cette opération réussit et si le nombre de références fortes est différent de zéro. Le paramètre *ppvObject* est défini sur la référence forte.

- Sinon, HRESULT qui indique la raison de l’échec de cette opération.

### <a name="remarks"></a>Notes

Définit le pointeur spécifié sur la valeur de référence forte actuelle si le nombre de références fortes est différent de zéro.

## <a name="weakreferencesetunknown"></a><a name="setunknown"></a>WeakReference :: Setunknown,

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

```cpp
void SetUnknown(
   _In_ IUnknown* unk
);
```

### <a name="parameters"></a>Paramètres

*unk*<br/>
Pointeur vers l' `IUnknown` interface d’un objet.

### <a name="remarks"></a>Notes

Définit la référence forte de l' `WeakReference` objet actuel sur le pointeur d’interface spécifié.

## <a name="weakreferenceweakreference"></a><a name="weakreference"></a>WeakReference :: WeakReference

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

```cpp
WeakReference();
```

### <a name="remarks"></a>Notes

Initialise une nouvelle instance de la classe `WeakReference`.

Le pointeur de référence forte pour l' `WeakReference` objet est initialisé à **`nullptr`** , et le nombre de références fortes est initialisé à 1.
