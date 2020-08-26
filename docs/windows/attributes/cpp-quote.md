---
title: cpp_quote (attribut COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.cpp_quote
helpviewer_keywords:
- cpp_quote attribute
ms.assetid: f75327ff-42bd-498b-9177-7ffa25427e1f
ms.openlocfilehash: 27be83d123b5433f79c4c8a702197fc6f9f1a753
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88833164"
---
# <a name="cpp_quote"></a>cpp_quote

Émet la chaîne spécifiée, sans les guillemets, dans le fichier. idl généré.

## <a name="syntax"></a>Syntaxe

```cpp
[ cpp_quote("statement") ];
```

### <a name="parameters"></a>Paramètres

*instruction*<br/>
Instruction C.

## <a name="remarks"></a>Notes

L’attribut **cpp_quote** C++ est utile si vous souhaitez placer une directive de préprocesseur dans un fichier. idl.

Vous pouvez également utiliser **cpp_quote** et générer un fichier. h dans le cadre de la compilation MIDL. Par exemple, si vous avez un fichier d’en-tête C++ qui utilise des attributs IDL C++, mais que vous ne pouvez pas utiliser ce fichier pour une tâche, vous pouvez le compiler pour créer un fichier. h généré par MIDL, que vous devez être en mesure d’utiliser.

L’attribut **cpp_quote** a les mêmes fonctionnalités que l’attribut MIDL [cpp_quote](/windows/win32/Midl/cpp-quote) .

## <a name="example"></a>Exemple

Consultez l’exemple de [double](dual.md) pour obtenir un exemple d’utilisation de **cpp_quote**.

## <a name="requirements"></a>Configuration requise

| Contexte d’attribut | Valeur |
|-|-|
|**S’applique à**|N'importe où|
|**Repeatable Read**|Non|
|**Attributs requis**|Aucun|
|**Attributs non valides**|Aucun|

Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs autonomes](stand-alone-attributes.md)
