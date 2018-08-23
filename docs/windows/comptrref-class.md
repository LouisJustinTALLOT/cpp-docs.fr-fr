---
title: ComPtrRef (classe) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::Details::ComPtrRef
dev_langs:
- C++
helpviewer_keywords:
- ComPtrRef class
ms.assetid: d6bdfd20-e977-45b4-9ac1-1b8efbdb77de
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: aaeb641fc7b2276567edfb30fd36c46db6cfc5ae
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42613687"
---
# <a name="comptrref-class"></a>ComPtrRef (classe)

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

## <a name="syntax"></a>Syntaxe

```cpp
template <
   typename T
>
class ComPtrRef : public ComPtrRefBase<T>;
```

#### <a name="parameters"></a>Paramètres

*T*  
Un [ComPtr\<T >](../windows/comptr-class.md) type ou un type dérivé, pas simplement l’interface représentée par le `ComPtr`.

## <a name="remarks"></a>Notes

Représente une référence à un objet de type `ComPtr<T>`.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[ComPtrRef::ComPtrRef, constructeur](../windows/comptrref-comptrref-constructor.md)|Initialise une nouvelle instance de la **ComPtrRef** classe à partir du pointeur spécifié vers un autre **ComPtrRef** objet.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[ComPtrRef::GetAddressOf, méthode](../windows/comptrref-getaddressof-method.md)|Récupère l’adresse d’un pointeur vers l’interface représentée par l’actuel **ComPtrRef** objet.|
|[ComPtrRef::ReleaseAndGetAddressOf, méthode](../windows/comptrref-releaseandgetaddressof-method.md)|Supprime l’actuel **ComPtrRef** de l’objet et retourne un pointeur-à-un-pointeur vers l’interface qui a été représenté par le **ComPtrRef** objet.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[ComPtrRef::operator InterfaceType**, opérateur](../windows/comptrref-operator-interfacetype-star-star-operator.md)|Supprime l’actuel **ComPtrRef** de l’objet et retourne un pointeur-à-un-pointeur vers l’interface qui a été représenté par le **ComPtrRef** objet.|
|[ComPtrRef::operator T*, opérateur](../windows/comptrref-operator-t-star-operator.md)|Retourne la valeur de la [ptr_](../windows/comptrrefbase-ptr-data-member.md) membre de données de l’objet ComPtrRef actuel.|
|[ComPtrRef::operator void**, opérateur](../windows/comptrref-operator-void-star-star-operator.md)|Supprime actuel **ComPtrRef** d’objet, convertit le pointeur vers l’interface qui a été représenté par le **ComPtrRef** objet sous la forme d’un pointeur à pointeur-à **void**, puis Retourne le pointeur de cast.|
|[ComPtrRef::operator*, opérateur](../windows/comptrref-operator-star-operator.md)|Récupère le pointeur vers l’interface représentée par l’actuel **ComPtrRef** objet.|
|[ComPtrRef::operator==, opérateur](../windows/comptrref-operator-equality-operator.md)|Indique si deux **ComPtrRef** objets sont égaux.|
|[ComPtrRef::operator!=, opérateur](../windows/comptrref-operator-inequality-operator.md)|Indique si deux **ComPtrRef** objets ne sont pas égaux.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`ComPtrRefBase`

`ComPtrRef`

## <a name="requirements"></a>Configuration requise

**En-tête :** client.h

**Namespace :** Microsoft::WRL::Details

## <a name="see-also"></a>Voir aussi

[Microsoft::WRL::Details, espace de noms](../windows/microsoft-wrl-details-namespace.md)