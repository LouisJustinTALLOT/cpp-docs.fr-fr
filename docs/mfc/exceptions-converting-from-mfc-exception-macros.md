---
title: 'Exceptions : Conversion à partir de Macros d’Exception MFC'
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
ms.openlocfilehash: 59b83438d5341fd6a139af64a2f365a739438741
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62394505"
---
# <a name="exceptions-converting-from-mfc-exception-macros"></a>Exceptions : Conversion à partir de Macros d’Exception MFC

Il s’agit d’une rubrique avancée.

Cet article explique comment convertir le code existant écrit avec les macros de Microsoft Foundation Class — **essayez**, **CATCH**, **lever**, et ainsi de suite, à utiliser la gestion d’exceptions C++ mots clés **essayez**, **catch**, et **lever**. Les rubriques traitées ici sont les suivantes :

- [Avantages de la conversion](#_core_advantages_of_converting)

- [Conversion de code avec les macros d’exception à utiliser des exceptions C++](#_core_doing_the_conversion)

##  <a name="_core_advantages_of_converting"></a> Avantages de la conversion

Probablement inutile convertir le code existant, bien que vous devez être conscient des différences entre les implémentations de macros dans MFC version 3.0 et les implémentations dans les versions antérieures. Ces différences et les modifications suivantes dans le comportement de code sont abordées dans [Exceptions : Modifications apportées aux Macros d’Exception dans la Version 3.0](../mfc/exceptions-changes-to-exception-macros-in-version-3-0.md).

Les principaux avantages de la conversion sont :

- Code qui utilise les mots clés de gestion des exceptions C++ se compile en un peu plus petits. EXE ou. DLL.

- Le C++ mots clés de gestion des exceptions sont plus polyvalents : Ils peuvent gérer les exceptions de n’importe quel type de données qui peuvent être copiés (**int**, **float**, **char**, et ainsi de suite), tandis que les macros ne gérer que les exceptions de classe `CException` et les classes dérivées à partir de celui-ci.

La principale différence entre les macros et les mots clés est que l’utilisation des macros « automatique » de code supprime une exception interceptée lorsque l’exception passe hors de portée. Code à l’aide de mots clés ne fait pas, donc vous devez supprimer explicitement une exception interceptée. Pour plus d’informations, consultez l’article [Exceptions : Interception et suppression d’Exceptions](../mfc/exceptions-catching-and-deleting-exceptions.md).

Une autre différence est la syntaxe. La syntaxe pour les macros et les mots clés diffère dans trois aspects :

1. Arguments de macro et les déclarations d’exception :

   Un **CATCH** appel de macro présente la syntaxe suivante :

   **CATCH(** *exception_class*, *exception_object_pointer_name* **)**

   Notez que la virgule entre le nom de classe et le nom de pointeur d’objet.

   La déclaration d’exception pour le **catch** mot clé utilise la syntaxe suivante :

   **catch(** *exception_type* *exception_name* **)**

   Cette instruction de déclaration d’exception indique le type d’exception catch bloquer des handles.

2. Délimitation des blocs catch :

   Avec les macros, le **CATCH** macro (avec ses arguments) commence le premier bloc catch ; le **AND_CATCH** macro commence les blocs d’interception et le **END_CATCH** (macro) met fin à la séquence des blocs catch.

   Avec les mots clés, le **catch** mot clé (avec sa déclaration d’exception) commence chaque bloc catch. Il n’existe aucun équivalent le **END_CATCH** macro ; fin avec son accolade fermante de ce bloc catch.

3. L’expression throw :

   Utilisent les macros **THROW_LAST** pour lever de nouveau l’exception actuelle. Le **lever** mot clé, sans aucun argument, a le même effet.

##  <a name="_core_doing_the_conversion"></a> Effectuer la Conversion

#### <a name="to-convert-code-using-macros-to-use-the-c-exception-handling-keywords"></a>Pour convertir le code à l’aide de macros à utiliser les mots clés de gestion des exceptions C++

1. Recherchez toutes les occurrences des macros MFC **essayez**, **CATCH**, **AND_CATCH**, **END_CATCH**, **lever**, et **THROW_LAST**.

2. Remplacer ou supprimer toutes les occurrences des macros suivantes :

   **Essayez** (remplacez-la par **essayez**)

   **INTERCEPTER** (remplacez-la par **catch**)

   **AND_CATCH** (remplacez-la par **catch**)

   **END_CATCH** (supprimer)

   **LEVER** (remplacez-la par **lever**)

   **THROW_LAST** (remplacez-la par **lever**)

3. Modifiez les arguments de macro afin qu’ils forment des déclarations d’exceptions valides.

   Par exemple, modifier

   [!code-cpp[NVC_MFCExceptions#6](../mfc/codesnippet/cpp/exceptions-converting-from-mfc-exception-macros_1.cpp)]

   par celle-ci :

   [!code-cpp[NVC_MFCExceptions#7](../mfc/codesnippet/cpp/exceptions-converting-from-mfc-exception-macros_2.cpp)]

4. Modifier le code dans les blocs catch afin qu’il supprime des objets d’exception en fonction des besoins. Pour plus d’informations, consultez l’article [Exceptions : Interception et suppression d’Exceptions](../mfc/exceptions-catching-and-deleting-exceptions.md).

Voici un exemple de code de gestion des exceptions à l’aide de macros d’exception MFC. Étant donné que le code dans l’exemple suivant utilise les macros, l’exception `e` est automatiquement supprimé :

[!code-cpp[NVC_MFCExceptions#8](../mfc/codesnippet/cpp/exceptions-converting-from-mfc-exception-macros_3.cpp)]

Le code dans l’exemple suivant utilise les mots clés des exceptions C++, donc l’exception doit être explicitement supprimée :

[!code-cpp[NVC_MFCExceptions#9](../mfc/codesnippet/cpp/exceptions-converting-from-mfc-exception-macros_4.cpp)]

Pour plus d’informations, consultez [Exceptions : À l’aide de Macros MFC et des Exceptions C++](../mfc/exceptions-using-mfc-macros-and-cpp-exceptions.md).

## <a name="see-also"></a>Voir aussi

[Gestion des exceptions](../mfc/exception-handling-in-mfc.md)<br/>
