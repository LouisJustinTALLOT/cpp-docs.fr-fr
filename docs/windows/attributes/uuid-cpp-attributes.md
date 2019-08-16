---
title: uuid (attributs C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.uuid
helpviewer_keywords:
- uuid attribute
ms.assetid: 90562a94-5e28-451b-a4b0-cadda7f66efe
ms.openlocfilehash: d644f59ac92bf4e39f191c291dd4fef626411c3d
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514950"
---
# <a name="uuid-c-attributes"></a>uuid (attributs C++)

Spécifie l’ID unique d’une classe ou d’une interface.

## <a name="syntax"></a>Syntaxe

```cpp
[ uuid(
   "uuid"
) ]
```

### <a name="parameters"></a>Paramètres

*uuid*<br/>
Identificateur unique 128 bits.

## <a name="remarks"></a>Notes

Si la définition d’une interface ou d’une classe ne spécifie pas l’attribut **UUID** C++ , C++ le compilateur Microsoft en fournit un. Lorsque vous spécifiez un **UUID**, vous devez inclure les guillemets.

Si vous ne spécifiez pas **UUID**, le compilateur génère le même GUID pour les interfaces ou les classes portant le même nom dans différents projets d’attributs sur un ordinateur.

Vous pouvez utiliser uuidgen. exe ou Guidgen. exe pour générer vos propres ID uniques. (Pour exécuter l’un de ces outils, cliquez sur **Démarrer** , puis sur **exécuter** dans le menu. Entrez ensuite le nom de l’outil requis.)

Lorsqu’il est utilisé dans un projet qui n’utilise pas également ATL, la spécification de l’attribut **UUID** revient à spécifier le modificateur [UUID](../../cpp/uuid-cpp.md) **_ _ declspec** . Pour récupérer l' **UUID** d’une classe, vous pouvez utiliser _ _ [uuidof](../../cpp/uuidof-operator.md)

## <a name="example"></a>Exemple

Consultez l’exemple [pouvant être lié](bindable.md) pour obtenir un exemple d’utilisation de l' **UUID**.

## <a name="requirements"></a>Configuration requise

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|**class**, **struct**, **interface**, **union**, **enum**|
|**Renouvelable**|Non|
|**Attributs requis**|Aucun|
|**Attributs non valides**|Aucun|

Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs d’interface](interface-attributes.md)<br/>
[Attributs de classe](class-attributes.md)<br/>
[Attributs Typedef, Enum, Union et Struct](typedef-enum-union-and-struct-attributes.md)<br/>
[uuid](/windows/win32/Midl/uuid)