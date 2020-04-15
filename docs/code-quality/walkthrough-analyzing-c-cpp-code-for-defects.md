---
title: 'Procédure pas à pas : Analyse du code C/CMD pour les défauts'
description: Démontre comment utiliser l’analyse de code avec Microsoft CMD dans Visual Studio.
ms.date: 04/14/2020
ms.topic: conceptual
helpviewer_keywords:
- C/C++, code analysis
- code analysis, walkthroughs
- code, analyzing C/C++
- code analysis tool, walkthroughs
ms.openlocfilehash: fe9b3775199b2a18cf940b99e87852350f1fbea9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370216"
---
# <a name="walkthrough-analyzing-cc-code-for-defects"></a>Procédure pas à pas : Analyse du code C/CMD pour les défauts

Cette procédure pas à pas montre comment analyser le code C/CMD pour les défauts de code potentiels. Il utilise les outils d’analyse de code pour le code C/CM.

Dans cette procédure pas à pas, vous :

- Exécuter l’analyse de code sur le code natif.
- Analyser les avertissements de défaut de code.
- Traiter l’avertissement comme une erreur.
- Annoter le code source pour améliorer l’analyse des défauts de code.

## <a name="prerequisites"></a>Prérequis

- Une copie de [l’échantillon CppDemo](../code-quality/demo-sample.md).
- Compréhension de base du C/CMD.

## <a name="run-code-analysis-on-native-code"></a>Analyse de code d’exécution sur le code indigène

### <a name="to-run-code-defect-analysis-on-native-code"></a>Pour exécuter l’analyse des défauts de code sur le code natif

::: moniker range=">=vs-2019"

1. Ouvrez la solution CppDemo dans Visual Studio.

     La solution CppDemo peuple maintenant **Solution Explorer**.

1. Sur le menu **Build,** choisissez **Rebuild Solution**.

     La solution se construit sans aucune erreur ou avertissement.

1. Dans **Solution Explorer**, sélectionnez le projet CodeDefects.

1. Sur le menu du **projet,** choisissez **Propriétés**.

     La boîte de dialogue **CodeDefects Property Pages** est affichée.

1. Sélectionnez la page de propriété **Code Analysis.**

1. Modifier **l’analyse de code d’activation sur la** propriété Build à **Oui**. Choisissez **OK** pour enregistrer vos modifications.

1. Reconstruire le projet CodeDefects.

     Les avertissements d’analyse de code sont affichés dans la fenêtre **de la liste d’erreurs.**

::: moniker-end

::: moniker range="<=vs-2017"

1. Ouvrez la solution CppDemo dans Visual Studio.

     La solution CppDemo peuple maintenant **Solution Explorer**.

1. Sur le menu **Build,** choisissez **Rebuild Solution**.

     La solution se construit sans aucune erreur ou avertissement.

     > [!NOTE]
     > Dans Visual Studio 2017, vous pouvez `E1097 unknown attribute "no_init_all"` voir un avertissement fallacieux dans le moteur IntelliSense. Vous pouvez ignorer cet avertissement sans problème.

1. Dans **Solution Explorer**, sélectionnez le projet CodeDefects.

1. Sur le menu du **projet,** choisissez **Propriétés**.

     La boîte de dialogue **CodeDefects Property Pages** est affichée.

1. Sélectionnez la page de propriété **Code Analysis.**

1. Sélectionnez l’analyse de code Active sur la case à cocher **Build.** Choisissez **OK** pour enregistrer vos modifications.

1. Reconstruire le projet CodeDefects.

     Les avertissements d’analyse de code sont affichés dans la fenêtre **de la liste d’erreurs.**

::: moniker-end

### <a name="to-analyze-code-defect-warnings"></a>Analyser les avertissements de défaut de code

1. Sur le menu **View,** choisissez **La liste d’erreurs**.

     Cet élément de menu peut ne pas être visible. Cela dépend du profil du développeur que vous avez choisi dans Visual Studio. Vous devrez peut-être pointer vers **d’autres Fenêtres** sur le menu **View,** puis choisir **la liste d’erreurs**.

1. Dans la fenêtre de la **liste d’erreurs,** cliquez double sur l’avertissement suivant :

     C6230: Casting implicite entre les types sémantically différents: en utilisant HRESULT dans un contexte Boolean.

     L’éditeur de code affiche la ligne `bool ProcessDomain()`qui a causé l’avertissement à l’intérieur de la fonction . Cet avertissement indique `HRESULT` qu’un est utilisé dans une déclaration «si» où un résultat Boolean est prévu. C’est généralement une erreur, `S_OK` parce que lorsque le HRESULT est retourné d’une fonction, il `false`indique le succès, mais lorsqu’il est converti en une valeur boolean, il évalue à .

1. Corrigez cet avertissement `SUCCEEDED` en utilisant la `true` macro, qui se convertit au moment où une valeur de `HRESULT` retour indique le succès. Votre code doit ressembler au code suivant :

   ```cpp
   if (SUCCEEDED(ReadUserAccount()))
   ```

1. Dans la **liste d’erreurs**, double-cliquez sur l’avertissement suivant:

     C6282: Opérateur incorrect : affectation de constante dans le contexte boolean. Envisagez plutôt d’utiliser le ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' '

1. Corrigez cet avertissement en testant l’égalité. Votre code doit ressembler au code suivant :

   ```cpp
   if ((len == ACCOUNT_DOMAIN_LEN) || (g_userAccount[len] != L'\\'))
   ```

1. Corrigez les avertissements C6001 restants `i` `j` dans la **liste d’erreurs** en parasissant et à 0.

1. Reconstruire le projet CodeDefects.

     Le projet se construit sans avertissements ni erreurs.

## <a name="correct-source-code-annotation-warnings"></a>Avertissements corrects d’annotation de code source

### <a name="to-enable-the-source-code-annotation-warnings-in-annotationc"></a>Pour activer les avertissements d’annotation du code source dans annotation.c

::: moniker range=">=vs-2019"

1. Dans Solution Explorer, sélectionnez le projet Annotations.

1. Sur le menu du **projet,** choisissez **Propriétés**.

     La boîte de dialogue **Annotations Property Pages** est affichée.

1. Sélectionnez la page de propriété **Code Analysis.**

1. Modifier **l’analyse de code d’activation sur la** propriété Build à **Oui**. Choisissez **OK** pour enregistrer vos modifications.

::: moniker-end

::: moniker range="<=vs-2017"

1. Dans Solution Explorer, sélectionnez le projet Annotations.

1. Sur le menu du **projet,** choisissez **Propriétés**.

     La boîte de dialogue **Annotations Property Pages** est affichée.

1. Sélectionnez la page de propriété **Code Analysis.**

1. Sélectionnez l’analyse de code Active sur la case à cocher **Build.** Choisissez **OK** pour enregistrer vos modifications.

::: moniker-end

### <a name="to-correct-the-source-code-annotation-warnings-in-annotationc"></a>Pour corriger les avertissements d’annotation du code source dans annotation.c

1. Reconstruire le projet Annotations.

1. Sur le menu **Build,** choisissez **l’analyse du code d’exécution sur annotations**.

1. Dans la **liste d’erreurs**, double-cliquez sur l’avertissement suivant:

     C6011: Déférence NULL pointeur 'newNode'.

     Cet avertissement indique l’échec de l’appelant à vérifier la valeur de retour. Dans ce cas, `AllocateNode` un appel pourrait retourner une valeur NULL. Voir le fichier d’en-tête annotations.h pour la déclaration de fonction pour `AllocateNode`.

1. Le curseur se trouve sur l’emplacement du dossier annotations.cpp où l’avertissement s’est produit.

1. Pour corriger cet avertissement, utilisez une instruction « si » pour tester la valeur de retour. Votre code doit ressembler au code suivant :

   ```cpp
   LinkedList* newNode = AllocateNode();
   if (nullptr != newNode)
   {
       newNode->data = value;
       newNode->next = 0;
       node->next = newNode;
   }
   ```

1. Reconstruire le projet Annotations.

     Le projet se construit sans avertissements ni erreurs.

## <a name="use-source-code-annotation-to-discover-more-issues"></a>Utiliser l’annotation du code source pour découvrir d’autres problèmes

### <a name="to-use-source-code-annotation"></a>Utiliser l’annotation du code source

1. Annoter les paramètres formels et `AddTail` la valeur de retour de la fonction pour indiquer que les valeurs de pointeur peuvent être nulles :

   ```cpp
   _Ret_maybenull_ LinkedList* AddTail(_Maybenull_ LinkedList* node, int value)
   ```

1. Dans le menu **Générer**, choisissez **Exécuter l’analyse du code sur la solution**.

1. Dans la **liste d’erreurs**, double-cliquez sur l’avertissement suivant:

     C6011: Déférence NULL pointeur 'nœud'.

     Cet avertissement indique que le nœud passé dans la fonction peut être nul.

1. Pour corriger cet avertissement, utilisez une déclaration « si » au début de la fonction pour tester la valeur passée. Votre code doit ressembler au code suivant :

   ```cpp
   if (nullptr == node)
   {
        return nullptr;
   }
   ```

1. Dans le menu **Générer**, choisissez **Exécuter l’analyse du code sur la solution**.

     Le projet se construit maintenant sans avertissements ni erreurs.

## <a name="see-also"></a>Voir aussi

[Procédure pas à pas : Analyse du code géré pour les défauts de code](/visualstudio/code-quality/walkthrough-analyzing-managed-code-for-code-defects)\
[Analyse du code pour C/C++](../code-quality/code-analysis-for-c-cpp-overview.md)
