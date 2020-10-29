---
title: 'Procédure pas à pas : analyse du code C/C++ pour les erreurs'
description: Montre comment utiliser l’analyse du code avec Microsoft C++ dans Visual Studio.
ms.date: 04/14/2020
ms.topic: conceptual
helpviewer_keywords:
- C/C++, code analysis
- code analysis, walkthroughs
- code, analyzing C/C++
- code analysis tool, walkthroughs
ms.openlocfilehash: bb81ca376651c17c760ee776510303efaa13fd9a
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92924779"
---
# <a name="walkthrough-analyzing-cc-code-for-defects"></a>Procédure pas à pas : analyse du code C/C++ pour les erreurs

Cette procédure pas à pas montre comment analyser du code C/C++ pour identifier les erreurs de code potentielles. Il utilise les outils d’analyse du code pour le code C/C++.

Dans cette procédure pas à pas, vous allez :

- Exécutez l’analyse du code sur du code natif.
- Analyser les avertissements de défaut de code.
- Traiter l’avertissement comme une erreur.
- Annoter le code source pour améliorer l’analyse des erreurs de code.

## <a name="prerequisites"></a>Conditions préalables requises

- Une copie de l' [exemple CppDemo](../code-quality/demo-sample.md).
- Connaissances de base de C/C++.

## <a name="run-code-analysis-on-native-code"></a>Exécuter l’analyse du code sur du code natif

### <a name="to-run-code-defect-analysis-on-native-code"></a>Pour exécuter l’analyse des erreurs de code sur du code natif

::: moniker range=">=msvc-160"

1. Ouvrez la solution CppDemo dans Visual Studio.

     La solution CppDemo remplit maintenant **Explorateur de solutions** .

1. Dans le menu **générer** , choisissez **régénérer la solution** .

     La solution est générée sans erreurs ou avertissements.

1. Dans **Explorateur de solutions** , sélectionnez le projet CodeDefects.

1. Dans le menu **projet** , choisissez **Propriétés** .

     La boîte de dialogue **pages de propriétés de CodeDefects** s’affiche.

1. Sélectionnez la page de propriétés **analyse du code** .

1. Modifiez la propriété **activer l’analyse du code sur la build** sur **Oui** . Choisissez **OK** pour enregistrer vos modifications.

1. Régénérez le projet CodeDefects.

     Les avertissements liés à l’analyse du code s’affichent dans la fenêtre **liste d’erreurs** .

::: moniker-end

::: moniker range="<=msvc-150"

1. Ouvrez la solution CppDemo dans Visual Studio.

     La solution CppDemo remplit maintenant **Explorateur de solutions** .

1. Dans le menu **générer** , choisissez **régénérer la solution** .

     La solution est générée sans erreurs ou avertissements.

     > [!NOTE]
     > Dans Visual Studio 2017, vous pouvez voir un avertissement parasite `E1097 unknown attribute "no_init_all"` dans le moteur IntelliSense. Vous pouvez ignorer cet avertissement sans problème.

1. Dans **Explorateur de solutions** , sélectionnez le projet CodeDefects.

1. Dans le menu **projet** , choisissez **Propriétés** .

     La boîte de dialogue **pages de propriétés de CodeDefects** s’affiche.

1. Sélectionnez la page de propriétés **analyse du code** .

1. Activez la case à cocher **activer l’analyse du code sur la build** . Choisissez **OK** pour enregistrer vos modifications.

1. Régénérez le projet CodeDefects.

     Les avertissements liés à l’analyse du code s’affichent dans la fenêtre **liste d’erreurs** .

::: moniker-end

### <a name="to-analyze-code-defect-warnings"></a>Pour analyser les avertissements de défauts de code

1. Dans le menu **affichage** , choisissez **liste d’erreurs** .

     Cet élément de menu peut ne pas être visible. Cela dépend du profil de développeur que vous avez choisi dans Visual Studio. Vous devrez peut-être pointer sur **autres fenêtres** dans le menu **affichage** , puis choisir **liste d’erreurs** .

1. Dans la fenêtre **liste d’erreurs** , double-cliquez sur l’avertissement suivant :

     C6230 : cast implicite entre les types sémantiquement différents : utilisation de HRESULT dans un contexte booléen.

     L’éditeur de code affiche la ligne qui a provoqué l’avertissement à l’intérieur de la fonction `bool ProcessDomain()` . Cet avertissement indique qu’un `HRESULT` est utilisé dans une instruction’If’où un résultat booléen est attendu. Il s’agit généralement d’une erreur, car lorsque le `S_OK` HRESULT est retourné à partir d’une fonction, il indique la réussite, mais lorsqu’il est converti en une valeur booléenne, il prend la valeur **`false`** .

1. Corrigez cet avertissement à l’aide de la `SUCCEEDED` macro, qui convertit en **`true`** lorsqu’une `HRESULT` valeur de retour indique une réussite. Votre code doit ressembler au code suivant :

   ```cpp
   if (SUCCEEDED(ReadUserAccount()))
   ```

1. Dans la **liste d’erreurs** , double-cliquez sur l’avertissement suivant :

     C6282 : opérateur incorrect : assignation d’une constante dans un contexte booléen. Utilisez' = = 'à la place.

1. Corrigez cet avertissement en vérifiant l’égalité. Votre code doit ressembler au code suivant :

   ```cpp
   if ((len == ACCOUNT_DOMAIN_LEN) || (g_userAccount[len] != L'\\'))
   ```

1. Corrigez les avertissements C6001 restants dans le **liste d’erreurs** en initialisant `i` et en `j` 0.

1. Régénérez le projet CodeDefects.

     Le projet est généré sans avertissements ou erreurs.

## <a name="correct-source-code-annotation-warnings"></a>Corriger les avertissements d’annotation de code source

### <a name="to-enable-the-source-code-annotation-warnings-in-annotationc"></a>Pour activer les avertissements d’annotation de code source dans annotation. c

::: moniker range=">=msvc-160"

1. Dans Explorateur de solutions, sélectionnez le projet annotations.

1. Dans le menu **projet** , choisissez **Propriétés** .

     La boîte de dialogue **pages de propriétés des annotations** s’affiche.

1. Sélectionnez la page de propriétés **analyse du code** .

1. Modifiez la propriété **activer l’analyse du code sur la build** sur **Oui** . Choisissez **OK** pour enregistrer vos modifications.

::: moniker-end

::: moniker range="<=msvc-150"

1. Dans Explorateur de solutions, sélectionnez le projet annotations.

1. Dans le menu **projet** , choisissez **Propriétés** .

     La boîte de dialogue **pages de propriétés des annotations** s’affiche.

1. Sélectionnez la page de propriétés **analyse du code** .

1. Activez la case à cocher **activer l’analyse du code sur la build** . Choisissez **OK** pour enregistrer vos modifications.

::: moniker-end

### <a name="to-correct-the-source-code-annotation-warnings-in-annotationc"></a>Pour corriger les avertissements d’annotation de code source dans annotation. c

1. Régénérez le projet annotations.

1. Dans le menu **générer** , choisissez **exécuter l’analyse du code sur les annotations** .

1. Dans la **liste d’erreurs** , double-cliquez sur l’avertissement suivant :

     C6011 : suppression de la référence du pointeur NULL’newNode'.

     Cet avertissement indique un échec de la vérification par l’appelant de la valeur de retour. Dans ce cas, un appel à `AllocateNode` peut retourner une valeur null. Consultez le fichier d’en-tête annotations. h pour la déclaration de fonction pour `AllocateNode` .

1. Le curseur se trouve à l’emplacement dans le fichier annotations. cpp où l’avertissement s’est produit.

1. Pour corriger cet avertissement, utilisez une instruction’If’pour tester la valeur de retour. Votre code doit ressembler au code suivant :

   ```cpp
   LinkedList* newNode = AllocateNode();
   if (nullptr != newNode)
   {
       newNode->data = value;
       newNode->next = 0;
       node->next = newNode;
   }
   ```

1. Régénérez le projet annotations.

     Le projet est généré sans avertissements ou erreurs.

## <a name="use-source-code-annotation-to-discover-more-issues"></a>Utiliser l’annotation de code source pour découvrir d’autres problèmes

### <a name="to-use-source-code-annotation"></a>Pour utiliser l’annotation de code source

1. Annotez les paramètres formels et la valeur de retour de la fonction `AddTail` pour indiquer que les valeurs de pointeur peuvent être NULL :

   ```cpp
   _Ret_maybenull_ LinkedList* AddTail(_Maybenull_ LinkedList* node, int value)
   ```

1. Dans le menu **Générer** , choisissez **Exécuter l’analyse du code sur la solution** .

1. Dans la **liste d’erreurs** , double-cliquez sur l’avertissement suivant :

     C6011 : déréférencement du pointeur NULL’node'.

     Cet avertissement indique que le nœud passé dans la fonction peut avoir la valeur null.

1. Pour corriger cet avertissement, utilisez une instruction’If’au début de la fonction pour tester la valeur passée. Votre code doit ressembler au code suivant :

   ```cpp
   if (nullptr == node)
   {
        return nullptr;
   }
   ```

1. Dans le menu **Générer** , choisissez **Exécuter l’analyse du code sur la solution** .

     Le projet se génère désormais sans avertissements ou erreurs.

## <a name="see-also"></a>Voir aussi

[Procédure pas à pas : analyse du code managé pour les erreurs de code](/visualstudio/code-quality/walkthrough-analyzing-managed-code-for-code-defects)\
[Analyse du code pour C/C++](../code-quality/code-analysis-for-c-cpp-overview.md)
