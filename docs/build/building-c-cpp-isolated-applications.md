---
description: 'En savoir plus sur : génération d’applications isolées C/C++'
title: Génération d'applications isolées C/C++
ms.date: 05/06/2019
helpviewer_keywords:
- isolated applications [C++]
ms.assetid: 8a2fe4fa-0489-433e-bfc6-495844d8d73a
ms.openlocfilehash: a8cd99032c27d21efaec7f213c470017e52777c7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97163208"
---
# <a name="building-cc-isolated-applications"></a>Génération d'applications isolées C/C++

Une application isolée dépend uniquement d’assemblys côte à côte et est liée à ses dépendances à l’aide d’un manifeste. Il n’est pas nécessaire que votre application soit totalement isolée pour pouvoir s’exécuter correctement sur Windows ; Toutefois, en investissant pour rendre votre application totalement isolée, vous pouvez gagner du temps si vous avez besoin de traiter votre application à l’avenir. Pour plus d’informations sur les avantages de l’isolation totale de votre application, consultez [applications isolées](/windows/win32/SbsCs/isolated-applications).

Quand vous générez votre application C/C++ native à l’aide de Visual Studio, par défaut, le système de projet Visual Studio génère un fichier manifeste qui décrit les dépendances de votre application sur les bibliothèques Visual Studio. S’il s’agit des seules dépendances de votre application, celle-ci devient une application isolée dès qu’elle est reconstruite avec Visual Studio. Si votre application utilise d’autres bibliothèques au moment de l’exécution, vous devrez peut-être régénérer ces bibliothèques en tant qu’assemblys côte à côte en suivant les étapes décrites dans [création d’assemblys côte à côte C/C++](building-c-cpp-side-by-side-assemblies.md).

## <a name="see-also"></a>Voir aussi

[Concepts d’applications isolées et d’assemblys côte à côte](concepts-of-isolated-applications-and-side-by-side-assemblies.md)<br/>
[Génération d’applications isolées C/C++ et d’assemblys côte à côte](building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)
