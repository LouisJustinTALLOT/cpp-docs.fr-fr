---
title: version (attribut de COM C++) | Microsoft Docs
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.version
dev_langs:
- C++
helpviewer_keywords:
- version attribute
- version information, version attribute
ms.assetid: db6ce5d8-82c2-4329-b1a8-8ca2f67342cb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ee79fca8784ade6509cfc5854eaaa165b68edee0
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48791013"
---
# <a name="version-c"></a>version (C++)

Identifie une version particulière entre plusieurs versions d’une classe.

## <a name="syntax"></a>Syntaxe

```cpp
[ version("version") ]
```

### <a name="parameters"></a>Paramètres

*version*<br/>
Le numéro de version de la `coclass`. Si non spécifié, 1.0 sera placé dans le fichier .idl.

## <a name="remarks"></a>Notes

Le **version** attribut C++ a les mêmes fonctionnalités que le [version](/windows/desktop/Midl/version) attribut MIDL et est transféré vers le fichier .idl généré.

## <a name="example"></a>Exemple

Consultez le [peut être liée](bindable.md) exemple pour un exemple d’utilisation de **version**.

## <a name="requirements"></a>Configuration requise

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|**classe**, **struct**|
|**Renouvelable**|Non|
|**Attributs requis**|**coclass**|
|**Attributs non valides**|Aucun.|

Pour plus d’informations sur les contextes d’attribut, consultez [contextes d’attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs de compilateur](compiler-attributes.md)<br/>
[Attributs de classe](class-attributes.md)  