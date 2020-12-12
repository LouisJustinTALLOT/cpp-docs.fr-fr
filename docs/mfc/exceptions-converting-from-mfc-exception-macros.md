---
description: 'En savoir plus sur : exceptions : conversion à partir de macros d’exception MFC'
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
ms.openlocfilehash: 83d4522dff902681e26a2bd098b46fea92bf1c6a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97290698"
---
# <a name="exceptions-converting-from-mfc-exception-macros"></a>Exceptions : conversion à partir de macros d'exception MFC

Il s’agit d’une rubrique avancée.

Cet article explique comment convertir le code existant écrit avec des macros Microsoft Foundation Class ( **try**, **catch**, **throw**, etc.) pour utiliser les mots clés de gestion des exceptions C++ **`try`** , **`catch`** et **`throw`** . Les sujets abordés sont les suivants :

- [Avantages de la conversion](#_core_advantages_of_converting)

- [Conversion de code avec des macros d’exception pour utiliser des exceptions C++](#_core_doing_the_conversion)

## <a name="advantages-of-converting"></a><a name="_core_advantages_of_converting"></a> Avantages de la conversion

Vous n’avez probablement pas besoin de convertir le code existant, bien que vous deviez connaître les différences entre les implémentations de macro dans MFC version 3,0 et les implémentations dans les versions antérieures. Ces différences et les modifications ultérieures du comportement du code sont décrites dans [exceptions : modifications apportées aux macros d’exception dans la Version 3,0](exceptions-changes-to-exception-macros-in-version-3-0.md).

Les principaux avantages de la conversion sont les suivants :

- Le code qui utilise les mots clés de gestion des exceptions C++ se compile en un légèrement plus petit. EXE ou. DLL.

- Les mots clés de gestion des exceptions C++ sont plus polyvalents : ils peuvent gérer les exceptions de tout type de données qui peut être copié ( **`int`** , **`float`** , **`char`** , etc.), tandis que les macros gèrent les exceptions uniquement de la classe `CException` et des classes dérivées de celui-ci.

La principale différence entre les macros et les mots clés est que le code qui utilise les macros supprime « automatiquement » une exception interceptée lorsque l’exception est hors de portée. Le code qui utilise les mots clés ne le fait pas, vous devez donc supprimer explicitement une exception interceptée. Pour plus d’informations, consultez l’article [exceptions : interception et suppression d’exceptions](exceptions-catching-and-deleting-exceptions.md).

La syntaxe est également différente. La syntaxe des macros et des mots clés diffère à trois égards :

1. Arguments de macro et déclarations d’exception :

   Un appel de macro **catch** a la syntaxe suivante :

   **Catch (** *exception_class*, *exception_object_pointer_name* **)**

   Notez la virgule entre le nom de la classe et le nom du pointeur de l’objet.

   La déclaration d’exception pour le **`catch`** mot clé utilise la syntaxe suivante :

   **catch (** *exception_type* *exception_name* **)**

   Cette instruction de déclaration d’exception indique le type d’exception géré par le bloc catch.

2. Délimitation des blocs catch :

   Avec les macros, la macro **catch** (avec ses arguments) commence le premier bloc catch. la macro **AND_CATCH** commence par les blocs catch suivants, et la macro **END_CATCH** met fin à la séquence de blocs catch.

   Avec les mots clés, le **`catch`** mot clé (avec sa déclaration d’exception) commence chaque bloc catch. Il n’existe aucun équivalent à la macro **END_CATCH** ; le bloc catch se termine par son accolade fermante.

3. Expression Throw :

   Les macros utilisent **THROW_LAST** pour lever à nouveau l’exception actuelle. Le **`throw`** mot clé, sans argument, a le même effet.

## <a name="doing-the-conversion"></a><a name="_core_doing_the_conversion"></a> Conversion en cours

#### <a name="to-convert-code-using-macros-to-use-the-c-exception-handling-keywords"></a>Pour convertir du code à l’aide de macros pour utiliser les mots clés de gestion des exceptions C++

1. Recherchez toutes les occurrences de la macro MFC **try**, **catch**, **AND_CATCH**, **END_CATCH**, **throw** et **THROW_LAST**.

2. Remplacez ou supprimez toutes les occurrences des macros suivantes :

   **Essayez** (remplacez-le par **`try`** )

   **Catch** (le remplacer par **`catch`** )

   **AND_CATCH** (remplacez-le par **`catch`** )

   **END_CATCH** (supprimer)

   **Throw** (remplacez-le par **`throw`** )

   **THROW_LAST** (remplacez-le par **`throw`** )

3. Modifiez les arguments de macro afin qu’ils forment des déclarations d’exception valides.

   Par exemple, changez

   [!code-cpp[NVC_MFCExceptions#6](codesnippet/cpp/exceptions-converting-from-mfc-exception-macros_1.cpp)]

   to

   [!code-cpp[NVC_MFCExceptions#7](codesnippet/cpp/exceptions-converting-from-mfc-exception-macros_2.cpp)]

4. Modifiez le code dans les blocs catch afin qu’il supprime les objets exception si nécessaire. Pour plus d’informations, consultez l’article [exceptions : interception et suppression d’exceptions](exceptions-catching-and-deleting-exceptions.md).

Voici un exemple de code de gestion des exceptions à l’aide de macros d’exception MFC. Notez que, étant donné que le code de l’exemple suivant utilise les macros, l’exception `e` est supprimée automatiquement :

[!code-cpp[NVC_MFCExceptions#8](codesnippet/cpp/exceptions-converting-from-mfc-exception-macros_3.cpp)]

Le code de l’exemple suivant utilise les mots clés d’exceptions C++, donc l’exception doit être supprimée explicitement :

[!code-cpp[NVC_MFCExceptions#9](codesnippet/cpp/exceptions-converting-from-mfc-exception-macros_4.cpp)]

Pour plus d’informations, consultez [exceptions : utilisation de macros MFC et d’exceptions C++](exceptions-using-mfc-macros-and-cpp-exceptions.md).

## <a name="see-also"></a>Voir aussi

[Gestion des exceptions](exception-handling-in-mfc.md)<br/>
