---
title: Procédure pas à pas :C++ analyse du code C/code pour les erreurs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- C/C++, code analysis
- code analysis, walkthroughs
- code, analyzing C/C++
- code analysis tool, walkthroughs
ms.openlocfilehash: 5fbdf9e223b3c1e1b8664de2018381958c458f45
ms.sourcegitcommit: 7bea0420d0e476287641edeb33a9d5689a98cb98
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/17/2020
ms.locfileid: "77418654"
---
# <a name="walkthrough-analyzing-cc-code-for-defects"></a>Procédure pas à pas :C++ analyse du code C/code pour les erreurs

Cette procédure pas à pas montre comment analyserC++ c/code pour identifier les erreurs de code potentielles à l’aideC++ de l’outil d’analyse du code pour c/code.

- Exécutez l’analyse du code sur du code natif.
- Analyser les avertissements de défaut de code.
- Traiter l’avertissement comme une erreur.
- Annoter le code source pour améliorer l’analyse des erreurs de code.

## <a name="prerequisites"></a>Conditions préalables requises

- Copie de l' [exemple de démonstration](../code-quality/demo-sample.md).
- Connaissances de base de CC++/.

### <a name="to-run-code-defect-analysis-on-native-code"></a>Pour exécuter l’analyse des erreurs de code sur du code natif

1. Ouvrez la solution de démonstration dans Visual Studio.

     La solution de démonstration remplit maintenant **Explorateur de solutions**.

1. Dans le menu **Générer**, cliquez sur **Régénérer la solution**.

     La solution est générée sans erreurs ou avertissements.

1. Dans **Explorateur de solutions**, sélectionnez le projet CodeDefects.

1. Dans le menu **Projet** , cliquez sur **Propriétés**.

     La boîte de dialogue **pages de propriétés de CodeDefects** s’affiche.

1. Cliquez sur **Analyse du code**.

1. Activez la case à cocher **activer l'C++ analyse du code pour C/on Build** .

1. Régénérez le projet CodeDefects.

     Les avertissements de l’analyse du code s’affichent dans la **liste d’erreurs**.

### <a name="to-analyze-code-defect-warnings"></a>Pour analyser les avertissements de défauts de code

1. Dans le menu **Affichage** , cliquez sur **Liste d'erreurs**.

     En fonction du profil de développeur que vous avez choisi dans Visual Studio, vous devrez peut-être pointer sur **autres fenêtres** dans le menu **affichage** , puis cliquez sur **liste d’erreurs**.

1. Dans la **liste d’erreurs**, double-cliquez sur l’avertissement suivant :

     avertissement C6230 : cast implicite entre les types sémantiquement différents : utilisation de HRESULT dans un contexte booléen.

     L’éditeur de code affiche la ligne qui a provoqué l’avertissement dans la `bool ProcessDomain()`de la fonction. Cet avertissement indique qu’un `HRESULT` est utilisé dans une instruction’If’où un résultat booléen est attendu.  Il s’agit en général d’une erreur, car lorsque la `S_OK` HRESULT est retournée par la fonction, cette opération indique une réussite, mais lorsqu’elle est convertie en valeur booléenne, elle prend la valeur `false`.

1. Corrigez cet avertissement à l’aide de la macro `SUCCEEDED`, qui convertit en `true` lorsqu’une `HRESULT` valeur de retour indique la réussite de l’opération. Votre code doit ressembler au code suivant :

   ```cpp
   if (SUCCEEDED (ReadUserAccount()) )
   ```

1. Dans la **liste d’erreurs**, double-cliquez sur l’avertissement suivant :

     AVERTISSEMENT C6282 : opérateur incorrect : assignation à une constante dans le contexte de test. Était = = prévu ?

1. Corrigez cet avertissement en vérifiant l’égalité. Votre code doit ressembler au code suivant :

   ```cpp
   if ((len == ACCOUNT_DOMAIN_LEN) || (g_userAccount[len] != '\\'))
   ```

### <a name="to-treat-warning-as-an-error"></a>Pour traiter l’avertissement comme une erreur

1. Dans le fichier bug. cpp, ajoutez l’instruction `#pragma` suivante au début du fichier pour traiter l’avertissement C6001 comme une erreur :

   ```cpp
   #pragma warning (error: 6001)
   ```

1. Régénérez le projet CodeDefects.

     Dans le **liste d’erreurs**, C6001 s’affiche à présent comme une erreur.

1. Corrigez les deux erreurs C6001 restantes dans le **liste d’erreurs** en initialisant `i` et `j` sur 0.

1. Régénérez le projet CodeDefects.

     Le projet est généré sans avertissements ou erreurs.

### <a name="to-correct-the-source-code-annotation-warnings-in-annotationc"></a>Pour corriger les avertissements d’annotation de code source dans annotation. c

1. Dans Explorateur de solutions, sélectionnez le projet annotations.

1. Dans le menu **Projet** , cliquez sur **Propriétés**.

     La boîte de dialogue **pages de propriétés des annotations** s’affiche.

1. Cliquez sur **Analyse du code**.

1. Cochez la case **activer l’analyse du codeC++ pour C/on Build** .

1. Régénérez le projet annotations.

1. Dans la **liste d’erreurs**, double-cliquez sur l’avertissement suivant :

     AVERTISSEMENT C6011 : suppression de la référence du pointeur NULL’newNode'.

     Cet avertissement indique un échec de la vérification par l’appelant de la valeur de retour. Dans ce cas, un appel à **AllocateNode** peut retourner une valeur null (consultez le fichier d’en-tête annotations. h pour la déclaration de fonction pour AllocateNode).

1. Ouvrez le fichier annotations. cpp.

1. Pour corriger cet avertissement, utilisez une instruction’If’pour tester la valeur de retour. Votre code doit ressembler au code suivant :

   ```cpp
   if (nullptr != newNode)
   {
       newNode->data = value;
       newNode->next = 0;
       node->next = newNode;
   }
   ```

1. Régénérez le projet annotations.

     Le projet est généré sans avertissements ou erreurs.

### <a name="to-use-source-code-annotation"></a>Pour utiliser l’annotation de code source

1. Annotez les paramètres formels et la valeur de retour de la fonction `AddTail` pour indiquer que les valeurs de pointeur peuvent être NULL :

   ```cpp
   _Ret_maybenull_ LinkedList* AddTail(_Maybenull_ LinkedList* node, int value)
   ```

1. Régénérez le projet annotations.

1. Dans la **liste d’erreurs**, double-cliquez sur l’avertissement suivant :

     AVERTISSEMENT C6011 : suppression de la référence du pointeur NULL’node'.

     Cet avertissement indique que le nœud passé dans la fonction peut avoir la valeur null, et indique le numéro de ligne où l’avertissement a été déclenché.

1. Pour corriger cet avertissement, utilisez une instruction’If’au début de la fonction pour tester la valeur passée. Votre code doit ressembler au code suivant :

   ```cpp
   if (nullptr == node)
   {
        return nullptr;
   }
   ```

1. Régénérez le projet annotations.

     Le projet se génère désormais sans avertissements ou erreurs.

## <a name="see-also"></a>Voir aussi

[Procédure pas à pas : analyse du code managé pour les erreurs de Code](/visualstudio/code-quality/walkthrough-analyzing-managed-code-for-code-defects)\
[Analyse du code pour C/C++](../code-quality/code-analysis-for-c-cpp-overview.md)
