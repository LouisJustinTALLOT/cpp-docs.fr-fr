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
ms.openlocfilehash: a3372a176a158dd9c89eb888c8deb0244eef9a84
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/01/2019
ms.locfileid: "58784734"
---
# <a name="weakreference-class"></a>WeakReference, classe

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

## <a name="syntax"></a>Syntaxe

```cpp
class WeakReference;
```

## <a name="remarks"></a>Notes

Représente un *référence faible* qui peut être utilisé avec le Windows Runtime ou le COM classique. Une référence faible représente un objet qui peut être accessible ou non.

Un `WeakReference` objet conserve un *référence forte*, qui est un pointeur vers un objet et un *décompte de références fort*, qui est le nombre de copies de la référence forte qui ont été distribuées par le `Resolve()` (méthode). Bien que le nombre de référence forte est différente de zéro, la référence forte est valide et l’objet est accessible. Lorsque le nombre de référence forte devient égal à zéro, la référence forte n’est pas valide et l’objet n’est pas accessible.

Un `WeakReference` objet est généralement utilisé pour représenter un objet dont l’existence est contrôlée par un thread externe ou une application. Par exemple, construisez un `WeakReference` objet à partir d’une référence à un objet fichier. Pendant que le fichier est ouvert, la référence forte est valide, mais si le fichier est fermé, la référence forte devient non valide.

Le `WeakReference` méthodes sont thread-safe.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

Nom                                                  | Description
----------------------------------------------------- | ---------------------------------------------------------------------------
[WeakReference::WeakReference](#weakreference)        | Initialise une nouvelle instance de la classe `WeakReference`.
[WeakReference :: ~ WeakReference](#tilde-weakreference) | Annule l’initialisation (détruit) l’instance actuelle de la `WeakReference` classe.

### <a name="public-methods"></a>M&#233;thodes publiques

Nom                                                                 | Description
-------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------
[WeakReference::DecrementStrongReference](#decrementstrongreference) | Décrémente le fort décompte de références actuel `WeakReference` objet.
[WeakReference::IncrementStrongReference](#incrementstrongreference) | Incrémente le nombre de référence forte d’actuel `WeakReference` objet.
[WeakReference::Resolve](#resolve)                                   | Définit le pointeur spécifié à la valeur actuelle de la référence forte si le nombre de référence forte est différente de zéro.
[WeakReference::SetUnknown](#setunknown)                             | Définit la référence forte d’actuel `WeakReference` objet au pointeur d’interface spécifié.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`WeakReference`

## <a name="requirements"></a>Configuration requise

**En-tête :** implements.h

**Espace de noms :** Microsoft::WRL::Details

## <a name="tilde-weakreference"></a>WeakReference :: ~ WeakReference

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

```cpp
virtual ~WeakReference();
```

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

Annule l’initialisation de l’instance actuelle de la `WeakReference` classe.

## <a name="decrementstrongreference"></a>WeakReference::DecrementStrongReference

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

```cpp
ULONG DecrementStrongReference();
```

### <a name="remarks"></a>Notes

Décrémente le fort décompte de références actuel `WeakReference` objet.

Lorsque le nombre de référence forte devient égal à zéro, la référence forte est définie sur `nullptr`.

### <a name="return-value"></a>Valeur de retour

Le nombre de référence forte décrémenté.

## <a name="incrementstrongreference"></a>WeakReference::IncrementStrongReference

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

```cpp
ULONG IncrementStrongReference();
```

### <a name="return-value"></a>Valeur de retour

Le nombre de référence forte incrémenté.

### <a name="remarks"></a>Notes

Incrémente le nombre de référence forte d’actuel `WeakReference` objet.

## <a name="resolve"></a>WeakReference::Resolve

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

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
Lorsque cette opération se termine, une copie de la référence forte actuelle si le nombre de référence forte est différente de zéro.

### <a name="return-value"></a>Valeur de retour

- S_OK si cette opération réussit et le nombre de référence forte est égal à zéro. Le *ppvObject* paramètre est défini sur `nullptr`.

- S_OK si cette opération réussit et le nombre de référence forte est différent de zéro. Le *ppvObject* paramètre est défini sur la référence forte.

- Sinon, un HRESULT qui indique la raison pour laquelle cette opération a échoué.

### <a name="remarks"></a>Notes

Définit le pointeur spécifié à la valeur actuelle de la référence forte si le nombre de référence forte est différente de zéro.

## <a name="setunknown"></a>WeakReference::SetUnknown

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

```cpp
void SetUnknown(
   _In_ IUnknown* unk
);
```

### <a name="parameters"></a>Paramètres

*unk*<br/>
Un pointeur vers le `IUnknown` interface d’un objet.

### <a name="remarks"></a>Notes

Définit la référence forte d’actuel `WeakReference` objet au pointeur d’interface spécifié.

## <a name="weakreference"></a>WeakReference::WeakReference

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

```cpp
WeakReference();
```

### <a name="remarks"></a>Notes

Initialise une nouvelle instance de la classe `WeakReference`.

Le pointeur de la référence forte pour la `WeakReference` objet est initialisé à `nullptr`, et le nombre de référence forte est initialisé à 1.
