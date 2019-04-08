---
title: 'Procédure : Créer des projets C++ vérifiables (C++ / c++ / CLI)'
ms.date: 11/04/2016
helpviewer_keywords:
- verifiable assemblies [C++], creating
- conversions, C++ projects
- Visual C++ projects
ms.assetid: 4ef2cc1a-e3e5-4d67-8d8d-9c614f8ec5d3
ms.openlocfilehash: de3742717bf55c53ab4007aaed18b6ce687fbede
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57817373"
---
# <a name="how-to-create-verifiable-c-projects-ccli"></a>Comment : créer des projets C++ vérifiables (C++ / c++ / CLI)

Les Assistants application Visual C++ ne créent pas de projets vérifiables.

> [!IMPORTANT]
> Déconseillé de Visual Studio 2015 et Visual Studio 2017 ne prend pas en charge la **/CLR : pure** et **/CLR : safe** la création de projets vérifiables. Si vous avez besoin du code vérifiable, nous vous recommandons de que vous traduisez votre code en C#.

Toutefois, si vous utilisez une version antérieure de l’ensemble d’outils du compilateur Visual C++ qui prend en charge **/CLR : pure** et **/CLR : safe**, projets peuvent être convertis pour être vérifiable. Cette rubrique décrit comment définir des propriétés du projet et modifier les fichiers sources du projet pour transformer vos projets Visual C++ pour produire des applications vérifiables.

## <a name="compiler-and-linker-settings"></a>Paramètres du compilateur et éditeur de liens

Par défaut, les projets .NET utilisent l’indicateur de compilateur/CLR et configurer le matériel cible x86 l’éditeur de liens. Pour le code vérifiable, vous devez utiliser l’indicateur/clr : safe, et vous devez demander à l’éditeur de liens pour générer du code MSIL au lieu d’en instructions machine natives.

### <a name="to-change-the-compiler-and-linker-settings"></a>Pour modifier les paramètres du compilateur et éditeur de liens

1. Afficher la Page de propriétés du projet. Pour plus d’informations, consultez [définir du compilateur et les propriétés de build](../build/working-with-project-properties.md).

1. Sur le **général** page sous le **propriétés de Configuration** nœud, définissez la **prise en charge du Common Language Runtime** propriété **Safe MSIL Common Language Prise en charge runtime (/ CLR : safe)**.

1. Sur le **avancé** page sous le **l’éditeur de liens** nœud, définissez la **Type d’Image CLR** propriété **forcer l’image IL sécurisée (/ CLRIMAGETYPE : safe)**.

## <a name="removing-native-data-types"></a>Suppression de types de données natifs

Étant donné que les types de données natifs sont non vérifiable, même s’ils ne sont pas réellement utilisés, vous devez supprimer tous les fichiers d’en-tête contenant des types natifs.

> [!NOTE]
> La procédure suivante s’applique aux projets Windows Forms Application (.NET) et une Application Console (.NET).

### <a name="to-remove-references-to-native-data-types"></a>Pour supprimer les références aux types de données natifs

1. Commentez tout dans le fichier Stdafx.h.

## <a name="configuring-an-entry-point"></a>Configuration d’un point d’entrée

Étant donné que les applications vérifiables ne peut pas utiliser les bibliothèques d’exécution C (CRT), ils ne peut pas dépendre de la bibliothèque CRT pour appeler la fonction principale comme point d’entrée standard. Cela signifie que vous devez explicitement fournir le nom de la fonction à appeler initialement à l’éditeur de liens. (Dans ce cas, Main() est utilisé au lieu de main() ou _tmain() pour indiquer un point d’entrée non-CRT, mais étant donné que le point d’entrée doit être spécifié explicitement, ce nom est arbitraire.)

> [!NOTE]
> Les procédures suivantes s’appliquent aux projets d’Application Console (.NET).

#### <a name="to-configure-an-entry-point"></a>Pour configurer un point d’entrée

1. Remplacez _tmain() Main() dans le fichier du projet .cpp principal.

1. Afficher la Page de propriétés du projet. Pour plus d’informations, consultez [définir du compilateur et les propriétés de build](../build/working-with-project-properties.md).

1. Sur le **avancé** page sous le **l’éditeur de liens** nœud, entrez `Main` en tant que le **Point d’entrée** valeur de propriété.

## <a name="see-also"></a>Voir aussi

- [Code pur et vérifiable (C++-CLI)](../dotnet/pure-and-verifiable-code-cpp-cli.md)
