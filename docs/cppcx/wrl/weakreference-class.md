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
ms.openlocfilehash: a80c0ec14da2a955a95ac84dd3975212ef20ae04
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374218"
---
# <a name="weakreference-class"></a>WeakReference, classe

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

## <a name="syntax"></a>Syntaxe

```cpp
class WeakReference;
```

## <a name="remarks"></a>Notes

Représente une *référence faible* qui peut être utilisée avec le Windows Runtime ou COM classique. Une référence faible représente un objet qui peut être accessible ou non.

Un `WeakReference` objet maintient une référence forte , qui est un pointeur à un objet, et un *nombre de références* *forte*, qui est le nombre d’exemplaires de la référence forte qui ont été distribués par la `Resolve()` méthode. Bien que le nombre de références solide soit non zéro, la référence forte est valide et l’objet est accessible. Lorsque le nombre de références solide devient nul, la référence forte est invalide et l’objet est inaccessible.

Un `WeakReference` objet est généralement utilisé pour représenter un objet dont l’existence est contrôlée par un thread ou une application externe. Par exemple, `WeakReference` construisez un objet à partir d’une référence à un objet de fichier. Pendant que le fichier est ouvert, la référence forte est valide, mais si le fichier est fermé, la référence forte devient non valide.

Les `WeakReference` méthodes sont sans danger de fil.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

Nom                                                  | Description
----------------------------------------------------- | ---------------------------------------------------------------------------
[Faiblereference::FaibleReference](#weakreference)        | Initialise une nouvelle instance de la classe `WeakReference`.
[Faiblereference::-WeakReference](#tilde-weakreference) | Désinitialise (détruit) l’instance actuelle `WeakReference` de la classe.

### <a name="public-methods"></a>M&#233;thodes publiques

Nom                                                                 | Description
-------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------
[FaibleReference::DecrementStrongReference](#decrementstrongreference) | Décrément le nombre de références `WeakReference` solide de l’objet actuel.
[FaibleReference::IncrementStrongReference](#incrementstrongreference) | Incréments le nombre de `WeakReference` références solide de l’objet actuel.
[FaibleReference::Resolve](#resolve)                                   | Définit le pointeur spécifié à la valeur de référence forte actuelle si le nombre de références solide est nonzero.
[FaibleReference::SetUnknown](#setunknown)                             | Définit la référence forte `WeakReference` de l’objet actuel au pointeur d’interface spécifié.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`WeakReference`

## <a name="requirements"></a>Spécifications

**En-tête:** implements.h

**Espace nom:** Microsoft::WRL::Details

## <a name="weakreferenceweakreference"></a><a name="tilde-weakreference"></a>Faiblereference::-WeakReference

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

```cpp
virtual ~WeakReference();
```

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

Désinitialise l’instance actuelle `WeakReference` de la classe.

## <a name="weakreferencedecrementstrongreference"></a><a name="decrementstrongreference"></a>FaibleReference::DecrementStrongReference

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

```cpp
ULONG DecrementStrongReference();
```

### <a name="remarks"></a>Notes

Décrément le nombre de références `WeakReference` solide de l’objet actuel.

Lorsque le nombre de références solide devient `nullptr`nul, la référence forte est définie à .

### <a name="return-value"></a>Valeur de retour

Le nombre de références fortement décrète.

## <a name="weakreferenceincrementstrongreference"></a><a name="incrementstrongreference"></a>FaibleReference::IncrementStrongReference

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

```cpp
ULONG IncrementStrongReference();
```

### <a name="return-value"></a>Valeur de retour

Le nombre de références fortement incrémenté.

### <a name="remarks"></a>Notes

Incréments le nombre de `WeakReference` références solide de l’objet actuel.

## <a name="weakreferenceresolve"></a><a name="resolve"></a>FaibleReference::Resolve

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
Lorsque cette opération se termine, une copie de la référence forte actuelle si le nombre de références solide n’est pas zéro.

### <a name="return-value"></a>Valeur de retour

- S_OK si cette opération est réussie et le nombre de références solide est nul. Le *paramètre ppvObject* est réglé pour `nullptr`.

- S_OK si cette opération est réussie et le nombre de références solide est nonzero. Le *paramètre ppvObject* est réglé à la référence forte.

- Sinon, un HRESULT qui indique la raison pour laquelle cette opération a échoué.

### <a name="remarks"></a>Notes

Définit le pointeur spécifié à la valeur de référence forte actuelle si le nombre de références solide est nonzero.

## <a name="weakreferencesetunknown"></a><a name="setunknown"></a>FaibleReference::SetUnknown

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

```cpp
void SetUnknown(
   _In_ IUnknown* unk
);
```

### <a name="parameters"></a>Paramètres

*Unk*<br/>
Un pointeur `IUnknown` à l’interface d’un objet.

### <a name="remarks"></a>Notes

Définit la référence forte `WeakReference` de l’objet actuel au pointeur d’interface spécifié.

## <a name="weakreferenceweakreference"></a><a name="weakreference"></a>Faiblereference::FaibleReference

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

```cpp
WeakReference();
```

### <a name="remarks"></a>Notes

Initialise une nouvelle instance de la classe `WeakReference`.

Le pointeur de `WeakReference` référence fort `nullptr`pour l’objet est initialisé à , et le nombre de référence fort est initialisé à 1.
