---
title: Génération d'applications isolées C/C++
ms.date: 11/04/2016
helpviewer_keywords:
- isolated applications [C++]
ms.assetid: 8a2fe4fa-0489-433e-bfc6-495844d8d73a
ms.openlocfilehash: 6ff9ada45a1ddd7c0aa1da62f6dd7f6a7b7bf371
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50534925"
---
# <a name="building-cc-isolated-applications"></a>Génération d'applications isolées C/C++

Une application isolée dépend uniquement les assemblys côte à côte et le lie à ses dépendances à l’aide d’un manifeste. Il n’est pas requis pour votre application soit complètement isolée afin de s’exécuter correctement sur Windows ; Toutefois, en investissant dans faire de votre application totalement isolée, vous pouvez gagner du temps si vous avez besoin votre application à l’avenir de service. Pour plus d’informations sur les avantages offerts isoler totalement votre application, consultez [Applications isolées](/windows/desktop/SbsCs/isolated-applications).

Lorsque vous générez votre application C/C++ native à l’aide de Visual C++, par défaut, Visual Studio, système de projet génère un fichier manifeste qui décrit les dépendances de votre application sur les bibliothèques Visual C++. S’il s’agit des seules dépendances votre application a, il devient alors une application isolée dès qu’elle est régénérée avec Visual Studio. Si votre application utilise d’autres bibliothèques lors de l’exécution, vous devrez peut-être régénérer ces bibliothèques en tant qu’assemblys côte à côte suivant les étapes décrites dans [génération C/C++ côte-à-côte d’assemblys](../build/building-c-cpp-side-by-side-assemblies.md).

## <a name="see-also"></a>Voir aussi

[Concepts d’applications isolées et d’assemblys côte à côte](../build/concepts-of-isolated-applications-and-side-by-side-assemblies.md)<br/>
[Génération d’applications isolées et d’assemblys côte à côte C/C++](../build/building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)