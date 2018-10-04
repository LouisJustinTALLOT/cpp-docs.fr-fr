---
title: UUID (attributs C++) | Microsoft Docs
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.uuid
dev_langs:
- C++
helpviewer_keywords:
- uuid attribute
ms.assetid: 90562a94-5e28-451b-a4b0-cadda7f66efe
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2bd15720c30c3a3f298e0094304205fd7fe5caeb
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48790692"
---
# <a name="uuid-c-attributes"></a>uuid (attributs C++)

Spécifie l’ID unique pour une classe ou interface.

## <a name="syntax"></a>Syntaxe

```cpp
[ uuid(
   "uuid"
) ]
```

### <a name="parameters"></a>Paramètres

*uuid*<br/>
Identificateur unique de 128 bits.

## <a name="remarks"></a>Notes

Si la définition d’une interface ou une classe ne spécifie pas le **uuid** attribut C++, puis le compilateur Visual C++ fournit un. Lorsque vous spécifiez un **uuid**, vous devez inclure les guillemets.

Si vous ne spécifiez pas **uuid**, le compilateur génère le même GUID pour les interfaces ou classes portant le même nom dans les projets d’attributs différentes sur un ordinateur.

Vous pouvez utiliser Uuidgen.exe ou Guidgen.exe pour générer votre propre ID unique. (Pour exécuter un de ces outils, cliquez sur **Démarrer** et cliquez sur **exécuter** dans le menu. Entrez le nom de l’outil requis.)

Lorsqu’il est utilisé dans un projet qui n’utilise pas également ATL, en spécifiant le **uuid** attribut est le même que si vous définissiez le [uuid](../../cpp/uuid-cpp.md) **__declspec** modificateur. Pour récupérer le **uuid** d’une classe, vous pouvez utiliser [__uuidof](../../cpp/uuidof-operator.md)

## <a name="example"></a>Exemple

Consultez le [peut être liée](bindable.md) exemple pour un exemple d’utilisation de **uuid**.

## <a name="requirements"></a>Configuration requise

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|**classe**, **struct**, **interface**, **union**, **enum**|
|**Renouvelable**|Non|
|**Attributs requis**|Aucun.|
|**Attributs non valides**|Aucun.|

Pour plus d’informations sur les contextes d’attribut, consultez [contextes d’attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs d’interface](interface-attributes.md)<br/>
[Attributs de classe](class-attributes.md)<br/>
[Attributs Typedef, Enum, Union et Struct](typedef-enum-union-and-struct-attributes.md)<br/>
[uuid](/windows/desktop/Midl/uuid)  