---
description: 'En savoir plus sur : Comment : créer des projets C++ vérifiables (C++/CLI)'
title: 'Comment : créer des projets C++ vérifiables (C++/CLI)'
ms.date: 11/04/2016
helpviewer_keywords:
- verifiable assemblies [C++], creating
- conversions, C++ projects
- Visual Studio C++ projects
ms.assetid: 4ef2cc1a-e3e5-4d67-8d8d-9c614f8ec5d3
ms.openlocfilehash: 5f3a84a4f87db5cf390dcfbad18f167108e0ff08
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97245991"
---
# <a name="how-to-create-verifiable-c-projects-ccli"></a>Comment : créer des projets C++ vérifiables (C++/CLI)

Visual C++ assistants application ne créent pas de projets vérifiables.

> [!IMPORTANT]
> Visual Studio 2015 déconseillé et Visual Studio 2017 ne prend pas en charge la création de projets vérifiables **/clr : pure** et **/clr : safe** . Si vous avez besoin de code vérifiable, nous vous recommandons de traduire votre code en C#.

Toutefois, si vous utilisez une version antérieure de l’ensemble d’outils du compilateur Microsoft C++ qui prend en charge **/clr : pure** et **/clr : safe**, les projets peuvent être convertis pour être vérifiables. Cette rubrique explique comment définir les propriétés du projet et modifier les fichiers sources du projet pour transformer vos projets Visual Studio C++ afin de produire des applications vérifiables.

## <a name="compiler-and-linker-settings"></a>Paramètres du compilateur et de l’éditeur de liens

Par défaut, les projets .NET utilisent l’indicateur de compilateur/CLR et configurent l’éditeur de liens pour cibler le matériel x86. Pour le code vérifiable, vous devez utiliser l’indicateur/CLR : safe, et vous devez demander à l’éditeur de liens de générer du code MSIL au lieu d’instructions machine natives.

### <a name="to-change-the-compiler-and-linker-settings"></a>Pour modifier les paramètres du compilateur et de l’éditeur de liens

1. Affichez la page de propriétés du projet. Pour plus d’informations, consultez [définir les propriétés du compilateur et de la build](../build/working-with-project-properties.md).

1. Sur la page **général** , sous le nœud **Propriétés de configuration** , affectez à la propriété **prise en charge du Common Language Runtime** la valeur **prise en charge du Common Language Runtime MSIL sécurisé (/CLR : safe)**.

1. Sur la page **avancé** , sous le nœud **éditeur de liens** , définissez la propriété type d' **image CLR** sur **forcer l’image il sécurisée (/CLRIMAGETYPE : safe)**.

## <a name="removing-native-data-types"></a>Suppression de types de données natifs

Comme les types de données natifs ne sont pas vérifiables, même s’ils ne sont pas réellement utilisés, vous devez supprimer tous les fichiers d’en-tête contenant des types natifs.

> [!NOTE]
> La procédure suivante s’applique à Windows Forms projets d’application (.NET) et d’application console (.NET).

### <a name="to-remove-references-to-native-data-types"></a>Pour supprimer les références aux types de données natifs

1. Commentez tout dans le fichier stdafx. h.

## <a name="configuring-an-entry-point"></a>Configuration d’un point d’entrée

Étant donné que les applications vérifiables ne peuvent pas utiliser les bibliothèques Runtime C (CRT), elles ne peuvent pas dépendre de la bibliothèque CRT pour appeler la fonction main en tant que point d’entrée standard. Cela signifie que vous devez fournir explicitement le nom de la fonction à appeler initialement à l’éditeur de liens. (Dans ce cas, main () est utilisé à la place de main () ou _tmain () pour indiquer un point d’entrée non CRT, mais comme le point d’entrée doit être spécifié explicitement, ce nom est arbitraire.)

> [!NOTE]
> Les procédures suivantes s’appliquent aux projets d’application console (.NET).

#### <a name="to-configure-an-entry-point"></a>Pour configurer un point d’entrée

1. Remplacez _tmain () par main () dans le fichier main. cpp du projet.

1. Affichez la page de propriétés du projet. Pour plus d’informations, consultez [définir les propriétés du compilateur et de la build](../build/working-with-project-properties.md).

1. Dans la page **avancé** , sous le nœud **éditeur de liens** , entrez `Main` comme valeur de propriété de **point d’entrée** .

## <a name="see-also"></a>Voir aussi

- [Code pur et vérifiable (C++/CLI)](../dotnet/pure-and-verifiable-code-cpp-cli.md)
