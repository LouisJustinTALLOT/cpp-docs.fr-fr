---
title: Platform::iboxarray, Interface | Microsoft Docs
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- VCCORLIB/Namespace not found::Platform
- VCCORLIB/Namespace not found::Platform::Value
dev_langs:
- C++
helpviewer_keywords:
- Platform::IBoxArray
ms.assetid: 6cd82c9e-4230-4147-9edb-7a652875dbf1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 66e3ff5a2daf0ddef41ea478b55ca2fc67298c01
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44108446"
---
# <a name="platformiboxarray-interface"></a>Platform::IBoxArray, interface

`IBoxArray` est le wrapper pour les tableaux de types valeur passés via l'interface binaire d'application (ABI) ou stockés dans les collections d'éléments `Platform::Object^` tels que ceux dans les contrôles XAML.

## <a name="syntax"></a>Syntaxe

```cpp
template <typename T>
interface class IBoxArray
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Type de la valeur boxed dans chaque élément du tableau.

### <a name="remarks"></a>Notes

`IBoxArray` est le C + c++ / nom CX pour `Windows::Foundation::IReferenceArray`.

### <a name="members"></a>Membres

L'interface `IBoxArray` hérite de l'interface `IValueType` . `IBoxArray` a également ces membres :

|Méthode|Description|
|------------|-----------------|
|[Valeur](#value)|Retourne le tableau non converti par boxing qui a été précédemment enregistré dans cette instance `IBoxArray` .|

## <a name="value"></a> Iboxarray::value, propriété

Retourne la valeur qui a été enregistrée à l'origine dans cet objet.

### <a name="syntax"></a>Syntaxe

```cpp
property T Value {T get();}
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Type de la valeur boxed.

### <a name="property-valuereturn-value"></a>Valeur de propriété/valeur de retour

Retourne la valeur qui a été enregistrée à l'origine dans cet objet.

### <a name="remarks"></a>Notes

Pour obtenir un exemple, consultez [Boxing](../cppcx/boxing-c-cx.md).

## <a name="see-also"></a>Voir aussi

[Array et WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md)