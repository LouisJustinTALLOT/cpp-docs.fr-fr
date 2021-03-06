---
description: 'En savoir plus sur : boxing (C++/CLI)'
title: Boxing (C++/CLI)
ms.date: 11/04/2016
ms.assetid: f4ee27a8-6a34-432d-b9ec-39285d513b23
ms.openlocfilehash: 4914271dc5b1ae0bcee2a82b3cddb4433a2dc84f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97282586"
---
# <a name="boxing-ccli"></a>Boxing (C++/CLI)

Le boxing est le processus de conversion d’un type valeur en type `object` ou en n’importe quel type d’interface implémenté par le type valeur. Lorsque le common language runtime (CLR) convertit un type valeur, il encapsule la valeur dans un `System.Object` et le stocke sur le tas managé. L'unboxing extrait le type valeur de l'objet. La conversion boxing est implicite ; la conversion unboxing est explicite.

## <a name="related-articles"></a>Articles connexes

|Titre|Description|
|-----------|-----------------|
|[Comment : demander explicitement le boxing](../dotnet/how-to-explicitly-request-boxing.md)|Décrit comment demander explicitement le boxing sur une variable.|
|[Comment : utiliser gcnew pour créer des types valeur et utiliser le boxing implicite](../dotnet/how-to-use-gcnew-to-create-value-types-and-use-implicit-boxing.md)|Montre comment utiliser **`gcnew`** pour créer un type valeur boxed qui peut être placé sur le tas managé récupéré par le garbage collector.|
|[Procédure : Effectuer une conversion unbox](../dotnet/how-to-unbox.md)|Montre comment effectuer une unboxing et modifier une valeur.|
|[Conversions standard et Boxing implicite](../dotnet/standard-conversions-and-implicit-boxing.md)|Montre qu’une conversion standard est choisie par le compilateur sur une conversion qui requiert un boxing.|
|[Programmation .NET avec C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)|L’article de niveau supérieur pour la programmation .NET dans la documentation Visual C++.|
