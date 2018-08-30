---
title: cpp_quote | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.cpp_quote
dev_langs:
- C++
helpviewer_keywords:
- cpp_quote attribute
ms.assetid: f75327ff-42bd-498b-9177-7ffa25427e1f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: da9e378ff75ec67660b0c29a5765be88a2c06496
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43205664"
---
# <a name="cppquote"></a>cpp_quote

Émet la chaîne spécifiée, sans les caractères guillemet, dans le fichier .idl généré.

## <a name="syntax"></a>Syntaxe

```cpp
[ cpp_quote(
   "statement"
) ];
```

### <a name="parameters"></a>Paramètres

*statement*  
Une instruction C.

## <a name="remarks"></a>Notes

Le **cpp_quote** attribut C++ est utile si vous souhaitez placer une directive de préprocesseur dans un fichier .idl.

Vous pouvez également utiliser **cpp_quote** et générer un fichier .h dans le cadre de la compilation MIDL. Par exemple, si vous avez un fichier d’en-tête C++ qui utilise des attributs IDL du C++, mais ne pouvez pas utiliser ce fichier pour une tâche, puis vous pouvez compiler pour créer un fichier .h générés par MIDL, dont vous devez être en mesure d’utiliser.

Le **cpp_quote** attribut a les mêmes fonctionnalités que le [cpp_quote](/windows/desktop/Midl/cpp-quote) attribut MIDL.

## <a name="example"></a>Exemple

Consultez l’exemple de [double](../windows/dual.md) pour obtenir un exemple, utilisez l’utilisation de **cpp_quote**.

## <a name="requirements"></a>Configuration requise

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|N'importe où|
|**Renouvelable**|Non|
|**Attributs requis**|Aucun.|
|**Attributs non valides**|Aucun.|

Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](../windows/attribute-contexts.md).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](../windows/idl-attributes.md)  
[Attributs autonomes](../windows/stand-alone-attributes.md)  