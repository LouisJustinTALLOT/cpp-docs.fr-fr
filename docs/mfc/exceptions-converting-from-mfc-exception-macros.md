---
title: "Exceptions : conversion à partir de macros d'exception MFC"
ms.date: 08/27/2018
helpviewer_keywords:
- converting exceptions [MFC]
- exception objects [MFC]
- conversions [MFC], code written with MFC macros
- keywords [MFC], macros
- macrosv, C++ keywords
- exception objects [MFC], deleting
- CException class [MFC], deleting CException class objects
- exceptions [MFC], converting
- exceptions [MFC], deleting exception objects
- catch blocks [MFC], delimiting
- exception handling [MFC], converting exceptions
ms.assetid: bd3ac3b3-f3ce-4fdd-a168-a2cff13ed796
ms.openlocfilehash: 330f66b1f46542082637645ad53da016b434d4a2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372014"
---
# <a name="exceptions-converting-from-mfc-exception-macros"></a>Exceptions : conversion à partir de macros d'exception MFC

C’est un sujet avancé.

Cet article explique comment convertir le code existant écrit avec Microsoft Foundation Class macros - **TRY**, **CATCH**, **THROW**, et ainsi de suite - pour utiliser les mots clés de manipulation d’exception C **'essayer**, **attraper**, et **jeter**. Les sujets abordés sont les suivants :

- [Avantages de conversion](#_core_advantages_of_converting)

- [Convertir le code à l’exception des macros pour utiliser les exceptions C](#_core_doing_the_conversion)

## <a name="advantages-of-converting"></a><a name="_core_advantages_of_converting"></a>Avantages de la conversion

Vous n’avez probablement pas besoin de convertir le code existant, bien que vous devriez être conscient des différences entre les implémentations macro dans la version MFC 3.0 et les implémentations dans les versions antérieures. Ces différences et les modifications ultérieures du comportement du code sont discutées dans [Exceptions: Changes to Exception Macros in Version 3.0](../mfc/exceptions-changes-to-exception-macros-in-version-3-0.md).

Les principaux avantages de la conversion sont les principaux avantages de la conversion :

- Le code qui utilise les mots clés de manipulation d’exception de CMD compile à un peu plus petit . EXE ou . DLL.

- Les mots-clés de manipulation d’exception de CMD sont plus polyvalents : ils peuvent gérer les exceptions de n’importe quel type `CException` de données qui peuvent être copiés **(int,** **flotteur,** **char,** et ainsi de suite), tandis que les macros ne traitent des exceptions que de classe et de classes dérivées de celui-ci.

La principale différence entre les macros et les mots clés est que le code utilisant les macros "automatiquement" supprime une exception prise lorsque l’exception sort de portée. Code à l’aide des mots clés ne fonctionne pas, de sorte que vous devez supprimer explicitement une exception pris. Pour plus d’informations, voir l’article [Exceptions: Catching and Deleting Exceptions](../mfc/exceptions-catching-and-deleting-exceptions.md).

Une autre différence est la syntaxe. La syntaxe pour les macros et les mots clés diffère à trois égards :

1. Arguments macro et déclarations d’exception :

   Une macro-invocation **CATCH** a la syntaxe suivante :

   **CATCH (** *exception_class*, *exception_object_pointer_name* **)**

   Remarquez la virgule entre le nom de classe et le nom du pointeur d’objet.

   La déclaration d’exception pour le mot clé **de capture** utilise cette syntaxe :

   **capture (** *exception_type* *exception_name* **)**

   Cette déclaration d’exception indique le type d’exception que le bloc de capture gère.

2. Délimitation des blocs de capture :

   Avec les macros, la macro **CATCH** (avec ses arguments) commence le premier bloc de capture; la **macro AND_CATCH** commence blocs de capture suivants, et le **END_CATCH** macro met fin à la séquence de blocs de capture.

   Avec les mots clés, le mot clé **de capture** (avec sa déclaration d’exception) commence chaque bloc de capture. Il n’y a pas de contrepartie à la **macro END_CATCH;** le bloc de capture se termine par son corset de fermeture.

3. L’expression de lancer :

   Les macros utilisent **THROW_LAST** pour re-jeter l’exception actuelle. Le mot clé **de lancer,** sans argument, a le même effet.

## <a name="doing-the-conversion"></a><a name="_core_doing_the_conversion"></a>Faire la conversion

#### <a name="to-convert-code-using-macros-to-use-the-c-exception-handling-keywords"></a>Convertir le code à l’aide de macros pour utiliser les mots clés de manipulation des exceptions CMD

1. Localiser tous les événements des macros MFC **TRY**, **CATCH**, **AND_CATCH**, **END_CATCH**, **THROW**, et **THROW_LAST**.

2. Remplacer ou supprimer tous les occurrences des macros suivantes :

   **TRY** (Remplacez-le par **essai**)

   **CATCH** (Remplacez-le par **des prises**)

   **AND_CATCH** (Remplacez-le par **des prises)**

   **END_CATCH** (Supprimer)

   **THROW** (Remplacez-le par **lancer**)

   **THROW_LAST** (Remplacez-le par **lancer)**

3. Modifier les arguments macro afin qu’ils forment des déclarations d’exception valides.

   Par exemple, changez

   [!code-cpp[NVC_MFCExceptions#6](../mfc/codesnippet/cpp/exceptions-converting-from-mfc-exception-macros_1.cpp)]

   to

   [!code-cpp[NVC_MFCExceptions#7](../mfc/codesnippet/cpp/exceptions-converting-from-mfc-exception-macros_2.cpp)]

4. Modifier le code dans les blocs de capture afin qu’il supprime les objets d’exception au besoin. Pour plus d’informations, voir l’article [Exceptions: Catching and Deleting Exceptions](../mfc/exceptions-catching-and-deleting-exceptions.md).

Voici un exemple de code de manipulation d’exception utilisant des macros d’exception MFC. Notez que parce que le code dans l’exemple suivant utilise les macros, l’exception `e` est supprimée automatiquement:

[!code-cpp[NVC_MFCExceptions#8](../mfc/codesnippet/cpp/exceptions-converting-from-mfc-exception-macros_3.cpp)]

Le code dans l’exemple suivant utilise les mots clés d’exception CMD, de sorte que l’exception doit être explicitement supprimée:

[!code-cpp[NVC_MFCExceptions#9](../mfc/codesnippet/cpp/exceptions-converting-from-mfc-exception-macros_4.cpp)]

Pour plus d’informations, voir [Exceptions: Using MFC Macros and C ' Exceptions](../mfc/exceptions-using-mfc-macros-and-cpp-exceptions.md).

## <a name="see-also"></a>Voir aussi

[Gestion des exceptions](../mfc/exception-handling-in-mfc.md)<br/>
