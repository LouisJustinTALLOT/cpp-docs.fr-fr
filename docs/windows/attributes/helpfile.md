---
title: HelpFile (attribut COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.helpfile
helpviewer_keywords:
- helpfile attribute
ms.assetid: d75161c1-1363-4019-ae09-e7e3b8a3971e
ms.openlocfilehash: 641823779346bf5417ec0db26b83083fa949e960
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222119"
---
# <a name="helpfile"></a>helpfile

Définit le nom du fichier d’aide d’une bibliothèque de types.

## <a name="syntax"></a>Syntaxe

```cpp
[ helpfile("filename") ]
```

### <a name="parameters"></a>Paramètres

*extension*<br/>
Nom du fichier qui contient les rubriques d’aide.

## <a name="remarks"></a>Notes

L’attribut C++ **HelpFile** a les mêmes fonctionnalités que l’attribut MIDL [HelpFile](/windows/win32/Midl/helpfile) .

## <a name="example"></a>Exemple

Consultez l’exemple du [module](module-cpp.md) pour obtenir un exemple d’utilisation de **HelpFile**.

## <a name="requirements"></a>Spécifications

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S’applique à**|**interface**, **`typedef`** ,, **`class`** méthode,**`property`**|
|**Repeatable Read**|Non|
|**Attributs requis**|None|
|**Attributs non valides**|None|

Pour plus d'informations, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs d’interface](interface-attributes.md)<br/>
[Attributs de classe](class-attributes.md)<br/>
[Attributs de méthode](method-attributes.md)<br/>
[Attributs typedef, enum, Union et struct](typedef-enum-union-and-struct-attributes.md)<br/>
[helpcontext](helpcontext.md)<br/>
[helpstring](helpstring.md)
