---
title: Weakref, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::WeakRef
dev_langs:
- C++
helpviewer_keywords:
- WeakRef class
ms.assetid: 572be703-c641-496c-8af5-ad6164670ba1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 96aa076bb8285154f3b340e9e39ae36ed621522f
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42612731"
---
# <a name="weakref-class"></a>WeakRef, classe

Représente une *référence faible* qui peut être utilisée uniquement par le Windows Runtime, pas par le COM classique. Une référence faible représente un objet qui peut être accessible ou non.

## <a name="syntax"></a>Syntaxe

```cpp
class WeakRef : public ComPtr<IWeakReference>
```

## <a name="remarks"></a>Notes

Un **WeakRef** objet conserve un *référence forte*, qui est associé à un objet et peut être valide ou non valide. Appelez le `As()` ou `AsIID()` méthode pour obtenir une référence forte. Lorsque la référence forte est valide, elle peut accéder à l’objet associé. Lorsque la référence forte n’est pas valide (**nullptr**), l’objet associé n’est pas accessible.

Un **WeakRef** objet est généralement utilisé pour représenter un objet dont l’existence est contrôlée par un thread externe ou une application. Par exemple, construisez un **WeakRef** objet à partir d’une référence à un objet fichier. Pendant que le fichier est ouvert, la référence forte est valide, mais si le fichier est fermé, la référence forte devient non valide.

Notez qu’il existe un changement de comportement des méthodes [As](../windows/weakref-as-method.md), [AsIID](../windows/weakref-asiid-method.md) et [CopyTo](../windows/weakref-copyto-method.md) dans le Kit de développement logiciel SDK Windows 10. Précédemment, après avoir appelé une de ces méthodes, vous pouvez vérifier le WeakRef pour **nullptr** pour déterminer si une référence forte était obtenue avec succès, comme dans le code suivant :

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

Le code ci-dessus ne fonctionne pas lorsque vous utilisez le Kit de développement logiciel SDK Windows 10 (ou version ultérieure). Au lieu de cela, vérifiez le pointeur qui a été transmis pour **nullptr**.

```cpp
if (strongRef == nullptr)  
{
    wprintf(L"Couldn't get strong ref!");
}
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[WeakRef::WeakRef, constructeur](../windows/weakref-weakref-constructor.md)|Initialise une nouvelle instance de la **WeakRef** classe.|
|[WeakRef::~WeakRef, destructeur](../windows/weakref-tilde-weakref-destructor.md)|Annule l’initialisation de l’instance actuelle de la **WeakRef** classe.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[WeakRef::As, méthode](../windows/weakref-as-method.md)|Définit le texte spécifié `ComPtr` paramètre de pointeur pour représenter l’interface spécifiée.|
|[WeakRef::AsIID, méthode](../windows/weakref-asiid-method.md)|Définit le texte spécifié `ComPtr` paramètre de pointeur pour représenter l’ID de l’interface spécifiée.|
|[WeakRef::CopyTo, méthode](../windows/weakref-copyto-method.md)|Assigne un pointeur vers une interface, si disponible, à la variable pointeur spécifiée.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[WeakRef::operator&, opérateur](../windows/weakref-operator-ampersand-operator.md)|Retourne un `ComPtrRef` objet qui représente l’actuel **WeakRef** objet.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`ComPtr`

`WeakRef`

## <a name="requirements"></a>Configuration requise

**En-tête :** client.h

**Espace de noms :** Microsoft::WRL

## <a name="see-also"></a>Voir aussi

[Microsoft::WRL, espace de noms](../windows/microsoft-wrl-namespace.md)