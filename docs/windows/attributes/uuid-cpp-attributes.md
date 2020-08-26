---
title: uuid (attributs C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.uuid
helpviewer_keywords:
- uuid attribute
ms.assetid: 90562a94-5e28-451b-a4b0-cadda7f66efe
ms.openlocfilehash: 9ff8888c26945d7f118e71002e3b3290217b463c
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88843038"
---
# <a name="uuid-c-attributes"></a>uuid (attributs C++)

Spécifie l’ID unique d’une classe ou d’une interface.

## <a name="syntax"></a>Syntaxe

```cpp
[ uuid( "uuid" ) ]
```

### <a name="parameters"></a>Paramètres

*uuid*<br/>
Identificateur unique 128 bits.

## <a name="remarks"></a>Notes

Si la définition d’une interface ou d’une classe ne spécifie pas l' `uuid` attribut C++, le compilateur Microsoft C++ en fournit un. Lorsque vous spécifiez un `uuid` , vous devez inclure les guillemets.

Si vous ne spécifiez pas `uuid` , le compilateur génère le même GUID pour les interfaces ou les classes portant le même nom dans différents projets d’attributs sur un ordinateur.

Vous pouvez utiliser Uuidgen.exe ou Guidgen.exe pour générer vos propres ID uniques. (Pour exécuter l’un de ces outils, cliquez sur **Démarrer** , puis sur **exécuter** dans le menu. Entrez ensuite le nom de l’outil requis.)

Lorsqu’il est utilisé dans un projet qui n’utilise pas également ATL, la spécification de l' `uuid` attribut revient à [uuid](../../cpp/uuid-cpp.md) spécifier le **`__declspec`** modificateur UUID. Pour récupérer le `uuid` d’une classe, vous pouvez utiliser [__uuidof](../../cpp/uuidof-operator.md)

## <a name="example"></a>Exemple

Pour obtenir un exemple d’utilisation de, consultez l’exemple [pouvant être lié](bindable.md) `uuid` .

## <a name="requirements"></a>Configuration requise

| Contexte d’attribut | Valeur |
|-|-|
|**S’applique à**|`class`, `struct`, `interface`, `union`, `enum`|
|**Repeatable Read**|Non|
|**Attributs requis**|Aucun|
|**Attributs non valides**|Aucun|

Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs d’interface](interface-attributes.md)<br/>
[Attributs de classe](class-attributes.md)<br/>
[Attributs typedef, enum, Union et struct](typedef-enum-union-and-struct-attributes.md)<br/>
[uuid](/windows/win32/Midl/uuid)
