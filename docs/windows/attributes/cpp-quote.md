---
title: cpp_quote (C++ attribut COM)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.cpp_quote
helpviewer_keywords:
- cpp_quote attribute
ms.assetid: f75327ff-42bd-498b-9177-7ffa25427e1f
ms.openlocfilehash: 378435ced5a541785b7b32bc9d2f408034d5a2d8
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59024677"
---
# <a name="cppquote"></a>cpp_quote

Émet la chaîne spécifiée, sans les caractères guillemet, dans le fichier .idl généré.

## <a name="syntax"></a>Syntaxe

```cpp
[ cpp_quote("statement") ];
```

### <a name="parameters"></a>Paramètres

*statement*<br/>
Une instruction C.

## <a name="remarks"></a>Notes

Le **cpp_quote** C++ attribut est utile si vous souhaitez placer une directive de préprocesseur dans un fichier .idl.

Vous pouvez également utiliser **cpp_quote** et générer un fichier .h dans le cadre de la compilation MIDL. Par exemple, si vous avez un fichier d’en-tête C++ qui utilise des attributs IDL du C++, mais ne pouvez pas utiliser ce fichier pour une tâche, puis vous pouvez compiler pour créer un fichier .h générés par MIDL, dont vous devez être en mesure d’utiliser.

Le **cpp_quote** attribut a les mêmes fonctionnalités que le [cpp_quote](/windows/desktop/Midl/cpp-quote) attribut MIDL.

## <a name="example"></a>Exemple

Consultez l’exemple de [double](dual.md) pour obtenir un exemple, utilisez l’utilisation de **cpp_quote**.

## <a name="requirements"></a>Configuration requise

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|N'importe où|
|**Renouvelable**|Non|
|**Attributs requis**|Aucun.|
|**Attributs non valides**|Aucun.|

Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs autonomes](stand-alone-attributes.md)