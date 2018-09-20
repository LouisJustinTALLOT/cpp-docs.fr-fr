---
title: Boxing (C++ / c++ / CLI) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: f4ee27a8-6a34-432d-b9ec-39285d513b23
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 4c513b0148e2553440e02f9b0d255a0d5750e2d1
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46372510"
---
# <a name="boxing-ccli"></a>Boxing (C++/CLI)

Le boxing est le processus de conversion d’un type valeur au type `object` ou à n’importe quel type interface implémenté par le type de valeur. Lorsque le common language runtime (CLR) convertit un type valeur, qu’il encapsule la valeur dans un `System.Object` et les stocke sur le tas managé. L'unboxing extrait le type valeur de l'objet. La conversion boxing est implicite ; la conversion unboxing est explicite.

## <a name="related-articles"></a>Articles connexes

|Titre|Description|
|-----------|-----------------|
|[Guide pratique pour demander explicitement le boxing](../dotnet/how-to-explicitly-request-boxing.md)|Décrit comment demander explicitement le boxing sur une variable.|
|[Guide pratique pour utiliser gcnew pour créer des types valeur et utiliser un boxing implicite](../dotnet/how-to-use-gcnew-to-create-value-types-and-use-implicit-boxing.md)|Montre comment utiliser `gcnew` pour créer un type valeur boxed qui peut être placé sur le tas managé, le garbage collector.|
|[Guide pratique pour effectuer une conversion unbox](../dotnet/how-to-unbox.md)|Montre comment effectuer une conversion unboxing et modifier une valeur.|
|[Conversions standard et boxing implicite](../dotnet/standard-conversions-and-implicit-boxing.md)|Indique qu’une conversion standard est choisie par le compilateur via une conversion qui nécessite une conversion boxing.|
|[Programmation .NET avec C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)|L’article de niveau supérieur pour la programmation .NET dans la documentation de Visual C++.|