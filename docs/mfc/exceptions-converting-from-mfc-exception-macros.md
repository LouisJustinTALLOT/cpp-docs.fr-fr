---
title: 'Exceptions : Conversion à partir de Macros d’Exception MFC | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a386de558730e12bb8cf40da250c1d04dd4ff37a
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36931116"
---
# <a name="exceptions-converting-from-mfc-exception-macros"></a>Exceptions : conversion à partir de macros d'exception MFC
Il s’agit d’une rubrique avancée.  
  
 Cet article explique comment convertir le code existant écrit avec des macros de Microsoft Foundation Class : **essayez**, **CATCH**, **lever**, et ainsi de suite, pour utiliser la gestion d’exceptions C++ mots clés **essayez**, **catch**, et **lever**. Les rubriques traitées ici sont les suivantes :  
  
-   [Avantages de la conversion](#_core_advantages_of_converting)  
  
-   [Conversion de code avec des macros d’exception à utiliser des exceptions C++](#_core_doing_the_conversion)  
  
##  <a name="_core_advantages_of_converting"></a> Avantages de la conversion  
 Probablement inutile convertir le code existant, bien que vous devez être conscient des différences entre les implémentations de macros dans MFC version 3.0 et les implémentations dans les versions antérieures. Ces différences et les modifications suivantes dans le comportement du code sont décrites dans [Exceptions : modifications apportées aux Macros d’Exception dans la Version 3.0](../mfc/exceptions-changes-to-exception-macros-in-version-3-0.md).  
  
 Les principaux avantages de la conversion sont :  
  
-   Le code qui utilise les mots clés de gestion des exceptions C++ se compile en un peu plus petits. EXE ou. DLL.  
  
-   Les mots clés de gestion des exceptions C++ sont plus polyvalents : ils peuvent gérer les exceptions de tout type de données qui peuvent être copiés (**int**, **float**, **char**, et ainsi de suite), alors que le macros de gestion des exceptions uniquement de la classe `CException` et classes dérivées.  
  
 La principale différence entre les macros et les mots clés est que l’utilisation des macros « automatique » de code supprime une exception interceptée lorsque l’exception passe hors de portée. Code à l’aide de mots clés ne fait pas, vous devez supprimer explicitement une exception interceptée. Pour plus d’informations, consultez l’article [Exceptions : interception et suppression des Exceptions](../mfc/exceptions-catching-and-deleting-exceptions.md).  
  
 Une autre différence est la syntaxe. La syntaxe de macros et les mots clés diffère dans trois aspects :  
  
1.  Arguments de macros et déclarations de l’exception :  
  
     A **CATCH** invocation macro présente la syntaxe suivante :  
  
     **CATCH (** *classe_exception*, *nom_pointeur_objet_exception* **)**  
  
     Notez que la virgule entre le nom de classe et le nom de pointeur d’objet.  
  
     La déclaration d’exception pour le **catch** (mot clé) utilise la syntaxe suivante :  
  
     **catch (** *type_exception* *nom_exception ***)**  
  
     Cette instruction de déclaration d’exception indique le type d’exception catch bloquer les poignées.  
  
2.  Délimitation des blocs catch :  
  
     Avec les macros, le **CATCH** macro (avec ses arguments) commence le premier bloc catch ; le **AND_CATCH** macro commence les blocs catch suivants et le **END_CATCH** (macro) met fin à la séquence des blocs catch.  
  
     Avec les mots clés, les **catch** (mot clé) (avec sa déclaration d’exceptions) commence chaque bloc catch. Il n’existe aucun équivalent à la **END_CATCH** macro ; fin avec son accolade fermante de ce bloc catch.  
  
3.  L’expression throw :  
  
     Utilisent des macros **THROW_LAST** à lever à nouveau l’exception actuelle. Le **lever** (mot clé), sans argument, a le même effet.  
  
##  <a name="_core_doing_the_conversion"></a> La conversion  
  
#### <a name="to-convert-code-using-macros-to-use-the-c-exception-handling-keywords"></a>Convertir le code à l’aide de macros à utiliser les mots clés de gestion des exceptions C++  
  
1.  Recherchez toutes les occurrences des macros MFC **essayez**, **CATCH**, **AND_CATCH**, **END_CATCH**, **lever**, et **THROW_LAST**.  
  
2.  Remplacer ou supprimer toutes les occurrences des macros suivantes :  
  
     **Essayez** (remplacez-la par **essayez**)  
  
     **CATCH** (remplacez-la par **catch**)  
  
     **AND_CATCH** (remplacez-la par **catch**)  
  
     **END_CATCH** (supprimer)  
  
     **LEVER** (remplacez-la par **lever**)  
  
     **THROW_LAST** (remplacez-la par **lever**)  
  
3.  Modifier les arguments de macro de sorte qu’ils forment des déclarations d’exceptions valides.  
  
     Par exemple, modifier  
  
     [!code-cpp[NVC_MFCExceptions#6](../mfc/codesnippet/cpp/exceptions-converting-from-mfc-exception-macros_1.cpp)]  
  
     par celle-ci :  
  
     [!code-cpp[NVC_MFCExceptions#7](../mfc/codesnippet/cpp/exceptions-converting-from-mfc-exception-macros_2.cpp)]  
  
4.  Modifier le code dans les blocs catch afin qu’il supprime les objets d’exception si nécessaire. Pour plus d’informations, consultez l’article [Exceptions : interception et suppression des Exceptions](../mfc/exceptions-catching-and-deleting-exceptions.md).  
  
 Voici un exemple de code de gestion des exceptions à l’aide de macros d’exception MFC. Étant donné que le code dans l’exemple suivant utilise les macros, l’exception `e` est supprimé automatiquement :  
  
 [!code-cpp[NVC_MFCExceptions#8](../mfc/codesnippet/cpp/exceptions-converting-from-mfc-exception-macros_3.cpp)]  
  
 Le code dans l’exemple suivant utilise les mots clés des exceptions C++, l’exception doit être explicitement supprimée :  
  
 [!code-cpp[NVC_MFCExceptions#9](../mfc/codesnippet/cpp/exceptions-converting-from-mfc-exception-macros_4.cpp)]  
  
 Pour plus d’informations, consultez [Exceptions : utilisation des Macros MFC et des Exceptions C++](../mfc/exceptions-using-mfc-macros-and-cpp-exceptions.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des exceptions](../mfc/exception-handling-in-mfc.md)

