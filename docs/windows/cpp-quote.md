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
ms.openlocfilehash: 00dd1042195bd7593676021cc4f2f1153ec47844
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46432852"
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

*statement*<br/>
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

[Attributs IDL](../windows/idl-attributes.md)<br/>
[Attributs autonomes](../windows/stand-alone-attributes.md)  