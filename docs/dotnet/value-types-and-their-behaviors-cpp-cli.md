---
title: Types valeur et leurs comportements (C++ / c++ / CLI) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- value types
ms.assetid: 5cb872a6-1e0a-429d-853d-df4ab47e8f2a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 4d2d980e48a6f948c35faf0c4e42969795ef8dc7
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46404655"
---
# <a name="value-types-and-their-behaviors-ccli"></a>Types valeur et leurs comportements (C++/CLI)

Types valeur ont été modifiés de différentes manières d’Extensions managées pour C++ vers Visual C++. Dans cette section, nous examiner le type enum du CLR et le type de classe de valeur, ainsi que d’examiner le boxing et l’accès à l’instance boxed sur le tas CLR, mais aussi Examinons des pointeurs intérieurs et épingles. Modifications apportées au langage étendues ont été dans cette zone.

## <a name="in-this-section"></a>Dans cette section

[Type Enum du CLR](../dotnet/value-types-and-their-behaviors-cpp-cli.md)<br/>
Traite des modifications dans la déclaration et le comportement des enums.

[Conversion boxing implicite de types valeur](../dotnet/implicit-boxing-of-value-types.md)<br/>
Décrit la motivation pour une conversion boxing implicite de types valeur et des modifications conséquentes du comportement.

[Handle de suivi d’une valeur boxed](../dotnet/a-tracking-handle-to-a-boxed-value.md)<br/>
Décrit la conversion boxing implicite comment de valeur types traduit vers un handle de suivi à l’objet de valeur boxed.

[Sémantique de type valeur](../dotnet/value-type-semantics.md)<br/>
Traite des modifications apportées à la sémantique de type valeur, y compris les méthodes virtuelles héritées, des constructeurs de classe par défaut, des pointeurs intérieurs et des pointeurs épingle.

## <a name="see-also"></a>Voir aussi

[Initiation à la migration de C++/CLI](../dotnet/cpp-cli-migration-primer.md)<br/>
[Classes et structs](../windows/classes-and-structs-cpp-component-extensions.md)