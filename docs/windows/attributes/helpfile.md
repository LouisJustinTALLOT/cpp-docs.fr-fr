---
title: HelpFile (C++ attribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.helpfile
helpviewer_keywords:
- helpfile attribute
ms.assetid: d75161c1-1363-4019-ae09-e7e3b8a3971e
ms.openlocfilehash: 538cdbb38ac525cfee03a641f3e62e22a69f8e2b
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69501549"
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

## <a name="requirements"></a>Configuration requise

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|**interface**, **typedef**, **classe**, méthode, **propriété**|
|**Renouvelable**|Non|
|**Attributs requis**|Aucun|
|**Attributs non valides**|Aucun|

Pour plus d'informations, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs d’interface](interface-attributes.md)<br/>
[Attributs de classe](class-attributes.md)<br/>
[Attributs de méthode](method-attributes.md)<br/>
[Attributs Typedef, Enum, Union et Struct](typedef-enum-union-and-struct-attributes.md)<br/>
[helpcontext](helpcontext.md)<br/>
[helpstring](helpstring.md)