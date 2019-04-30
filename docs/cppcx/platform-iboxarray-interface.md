---
title: Platform::IBoxArray, interface
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Namespace not found::Platform
- VCCORLIB/Namespace not found::Platform::Value
helpviewer_keywords:
- Platform::IBoxArray
ms.assetid: 6cd82c9e-4230-4147-9edb-7a652875dbf1
ms.openlocfilehash: ea2517ad64cfd6742ef072d24e94a9b3899cea2d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62392074"
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
