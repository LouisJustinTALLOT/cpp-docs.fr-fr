---
title: HelpFile (C++ attribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.helpfile
helpviewer_keywords:
- helpfile attribute
ms.assetid: d75161c1-1363-4019-ae09-e7e3b8a3971e
ms.openlocfilehash: 1f928fa281c99630ad52ce1fde184c44e9387263
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80166976"
---
# <a name="helpfile"></a>helpfile

Définit le nom du fichier d’aide d’une bibliothèque de types.

## <a name="syntax"></a>Syntaxe

```cpp
[ helpfile("filename") ]
```

### <a name="parameters"></a>Paramètres

*filename*<br/>
Nom du fichier qui contient les rubriques d’aide.

## <a name="remarks"></a>Notes

L’attribut **HelpFile** C++ a les mêmes fonctionnalités que l’attribut MIDL [HelpFile](/windows/win32/Midl/helpfile) .

## <a name="example"></a>Exemple

Consultez l’exemple du [module](module-cpp.md) pour obtenir un exemple d’utilisation de **HelpFile**.

## <a name="requirements"></a>Spécifications

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|**interface**, **typedef**, **classe**, méthode, **propriété**|
|**Renouvelable**|Non|
|**Attributs requis**|None|
|**Attributs non valides**|None|

Pour plus d'informations, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs d’interface](interface-attributes.md)<br/>
[Attributs de classe](class-attributes.md)<br/>
[Attributs de méthode](method-attributes.md)<br/>
[Attributs Typedef, Enum, Union et Struct](typedef-enum-union-and-struct-attributes.md)<br/>
[helpcontext](helpcontext.md)<br/>
[helpstring](helpstring.md)
