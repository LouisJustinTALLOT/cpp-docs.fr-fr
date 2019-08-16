---
title: cpp_quote (C++ attribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.cpp_quote
helpviewer_keywords:
- cpp_quote attribute
ms.assetid: f75327ff-42bd-498b-9177-7ffa25427e1f
ms.openlocfilehash: 905c9fc41b1b42dffe9c7b39fae0b096cdc24950
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69501765"
---
# <a name="cpp_quote"></a>cpp_quote

Émet la chaîne spécifiée, sans les guillemets, dans le fichier. idl généré.

## <a name="syntax"></a>Syntaxe

```cpp
[ cpp_quote("statement") ];
```

### <a name="parameters"></a>Paramètres

*statement*<br/>
Instruction C.

## <a name="remarks"></a>Notes

L’attribut **cpp_quote** C++ est utile si vous souhaitez placer une directive de préprocesseur dans un fichier. idl.

Vous pouvez également utiliser **cpp_quote** et générer un fichier. h dans le cadre de la compilation MIDL. Par exemple, si vous avez un C++ fichier d’en- C++ tête qui utilise des attributs IDL mais que vous ne pouvez pas utiliser ce fichier pour une tâche, vous pouvez le compiler pour créer un fichier. h généré par MIDL, que vous devez être en mesure d’utiliser.

L’attribut **cpp_quote** a les mêmes fonctionnalités que l’attribut MIDL [cpp_quote](/windows/win32/Midl/cpp-quote) .

## <a name="example"></a>Exemples

Consultez l’exemple de [double](dual.md) pour obtenir un exemple d’utilisation de **cpp_quote**.

## <a name="requirements"></a>Configuration requise

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|N'importe où|
|**Renouvelable**|Non|
|**Attributs requis**|Aucun|
|**Attributs non valides**|Aucun|

Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs autonomes](stand-alone-attributes.md)