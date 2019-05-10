---
title: Génération d'applications isolées C/C++
ms.date: 05/06/2019
helpviewer_keywords:
- isolated applications [C++]
ms.assetid: 8a2fe4fa-0489-433e-bfc6-495844d8d73a
ms.openlocfilehash: 42192ad9388a8e69b70947c20c6fa7ee428a2bb9
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65220960"
---
# <a name="building-cc-isolated-applications"></a>Génération d'applications isolées C/C++

Une application isolée dépend uniquement les assemblys côte à côte et le lie à ses dépendances à l’aide d’un manifeste. Il n’est pas requis pour votre application soit complètement isolée afin de s’exécuter correctement sur Windows ; Toutefois, en investissant dans faire de votre application totalement isolée, vous pouvez gagner du temps si vous avez besoin votre application à l’avenir de service. Pour plus d’informations sur les avantages offerts isoler totalement votre application, consultez [Applications isolées](/windows/desktop/SbsCs/isolated-applications).

Lorsque vous générez votre natif C /C++ application à l’aide de Visual Studio, par défaut, le système de projet Visual Studio génère un fichier manifeste qui décrit les dépendances de votre application sur les bibliothèques Visual Studio. S’il s’agit des seules dépendances votre application a, il devient alors une application isolée dès qu’elle est régénérée avec Visual Studio. Si votre application utilise d’autres bibliothèques lors de l’exécution, vous devrez peut-être régénérer ces bibliothèques en tant qu’assemblys côte à côte suivant les étapes décrites dans [génération C/C++ côte-à-côte d’assemblys](building-c-cpp-side-by-side-assemblies.md).

## <a name="see-also"></a>Voir aussi

[Concepts d’applications isolées et d’assemblys côte à côte](concepts-of-isolated-applications-and-side-by-side-assemblies.md)<br/>
[Génération d’applications isolées et d’assemblys côte à côte C/C++](building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)
