---
title: Gestion des exceptions dans MFC
ms.date: 11/04/2016
helpviewer_keywords:
- DAO [MFC], exceptions
- assertions [MFC], When to use exceptions
- exception handling [MFC], MFC
- resource allocation exception
- resources [MFC], allocating
- keywords [MFC], exception handling
- errors [MFC], detected by assertions
- ODBC exceptions [MFC]
- serialization [MFC], exceptions
- Automation [MFC], exceptions
- exception macros [MFC]
- predefined exceptions [MFC]
- C++ exception handling [MFC], enabling
- C++ exception handling [MFC], MFC applications
- requests for unsupported services [MFC]
- database exceptions [MFC]
- archive exceptions [MFC]
- MFC, exceptions
- C++ exception handling [MFC], types of
- macros [MFC], exception handling
- abnormal program execution [MFC]
- OLE exceptions [MFC], MFC exception handling
- error handling [MFC], exceptions and
- class libraries [MFC], exception support
- exceptions [MFC], MFC macros vs. C++ keywords
- memory [MFC], out-of-memory exceptions
- Windows [MFC], resource allocation exceptions
- macros [MFC], MFC exception macros
- function calls [MFC], results
- out-of-memory exceptions [MFC]
ms.assetid: 0926627d-2ba7-44a6-babe-d851a4a2517c
ms.openlocfilehash: e8c0f1feba566ef9b961edcfacb9124830f9851d
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69508621"
---
# <a name="exception-handling-in-mfc"></a>Gestion des exceptions dans MFC

Cet article explique les mécanismes de gestion des exceptions disponibles dans MFC. Deux mécanismes sont disponibles:

- C++exceptions, disponibles dans MFC version 3,0 et versions ultérieures

- Les macros d’exception MFC, disponibles dans les versions 1,0 et ultérieures de MFC

Si vous écrivez une nouvelle application à l’aide de MFC, vous devez C++ utiliser le mécanisme. Vous pouvez utiliser le mécanisme basé sur les macros si votre application existante utilise déjà ce mécanisme de manière intensive.

Vous pouvez facilement convertir le code existant pour C++ utiliser des exceptions au lieu des macros d’exception MFC. Les avantages de la conversion de votre code et des instructions pour ce faire sont [décrits dans l’article exceptions: Conversion à partir de macros](../mfc/exceptions-converting-from-mfc-exception-macros.md)d’exception MFC.

Si vous avez déjà développé une application à l’aide des macros d’exception MFC, vous pouvez continuer à utiliser ces macros dans votre code C++ existant, tout en utilisant des exceptions dans votre nouveau code. Les exceptions [de l’article sont les suivantes: Les modifications apportées aux macros](../mfc/exceptions-changes-to-exception-macros-in-version-3-0.md) d’exception dans la version 3,0 fournissent des instructions pour ce faire.

> [!NOTE]
>  Pour activer C++ la gestion des exceptions dans votre code, C++ sélectionnez Activer les exceptions dans la page génération de codeC++ dans le dossier C/de la boîte de dialogue [pages de propriétés](../build/reference/property-pages-visual-cpp.md) du projet ou utilisez l’option de compilateur [/EHsc](../build/reference/eh-exception-handling-model.md) .

Cet article aborde les sujets suivants:

- [Quand utiliser des exceptions](#_core_when_to_use_exceptions)

- [Prise en charge des exceptions MFC](#_core_mfc_exception_support)

- [En savoir plus sur les exceptions](#_core_further_reading_about_exceptions)

##  <a name="_core_when_to_use_exceptions"></a>Quand utiliser des exceptions

Trois catégories de résultats peuvent se produire lorsqu’une fonction est appelée pendant l’exécution du programme: exécution normale, exécution erronée ou exécution anormale. Chaque catégorie est décrite ci-dessous.

- Exécution normale

   La fonction peut s’exécuter normalement et retourner. Certaines fonctions retournent un code de résultat à l’appelant, ce qui indique le résultat de la fonction. Les codes de résultat possibles sont définis de façon stricte pour la fonction et représentent la plage des résultats possibles de la fonction. Le code de résultat peut indiquer la réussite ou l’échec ou peut même indiquer un type particulier de défaillance qui se trouve dans la plage normale des attentes. Par exemple, une fonction d’état de fichier peut retourner un code qui indique que le fichier n’existe pas. Notez que le terme «code d’erreur» n’est pas utilisé, car un code de résultat représente l’un des nombreux résultats attendus.

- Exécution erronée

   L’appelant fait une erreur lors du passage des arguments à la fonction ou appelle la fonction dans un contexte inapproprié. Cette situation provoque une erreur et doit être détectée par une assertion pendant le développement du programme. (Pour plus d’informations sur les assertions, consultez [C/C++ ](/visualstudio/debugger/c-cpp-assertions)assertions.)

- Exécution anormale

   Une exécution anormale comprend des situations où des conditions en dehors du contrôle du programme, telles que de la mémoire insuffisante ou des erreurs d’e/s, influencent le résultat de la fonction. Les situations anormales doivent être gérées par l’interception et la levée d’exceptions.

L’utilisation d’exceptions est particulièrement appropriée pour une exécution anormale.

##  <a name="_core_mfc_exception_support"></a>Prise en charge des exceptions MFC

Que vous utilisiez C++ les exceptions directement ou utilisiez les macros d’exception MFC, vous utiliserez `CException`la [classe CException](../mfc/reference/cexception-class.md) ou des objets dérivés qui peuvent être levés par l’infrastructure ou par votre application.

Le tableau suivant présente les exceptions prédéfinies fournies par MFC.

|Exception (classe)|Signification|
|---------------------|-------------|
|[CMemoryException, classe](../mfc/reference/cmemoryexception-class.md)|Mémoire insuffisante|
|[CFileException, classe](../mfc/reference/cfileexception-class.md)|Exception de fichier|
|[CArchiveException, classe](../mfc/reference/carchiveexception-class.md)|Exception d’archivage/sérialisation|
|[CNotSupportedException, classe](../mfc/reference/cnotsupportedexception-class.md)|Réponse à la demande de service non pris en charge|
|[CResourceException, classe](../mfc/reference/cresourceexception-class.md)|Exception d’allocation de ressources Windows|
|[CDaoException, classe](../mfc/reference/cdaoexception-class.md)|Exceptions de base de données (classes DAO)|
|[CDBException, classe](../mfc/reference/cdbexception-class.md)|Exceptions de base de données (classes ODBC)|
|[COleException, classe](../mfc/reference/coleexception-class.md)|exceptions OLE|
|[COleDispatchException, classe](../mfc/reference/coledispatchexception-class.md)|Exceptions de dispatch (Automation)|
|[CUserException, classe](../mfc/reference/cuserexception-class.md)|Exception qui avertit l’utilisateur avec une boîte de message, puis lève une [classe de CException](../mfc/reference/cexception-class.md) générique|

> [!NOTE]
>  MFC prend en C++ charge les exceptions et les macros d’exception MFC. MFC ne prend pas directement en charge les gestionnaires d’exceptions structurées (SEH) Windows NT, comme indiqué dans [gestion structurée des exceptions](/windows/win32/debug/structured-exception-handling).

##  <a name="_core_further_reading_about_exceptions"></a>En savoir plus sur les exceptions

Les articles suivants expliquent comment utiliser la bibliothèque MFC pour la gestion des exceptions:

- [Exceptions : Interception et suppression d’exceptions](../mfc/exceptions-catching-and-deleting-exceptions.md)

- [Exceptions : Examen du contenu des exceptions](../mfc/exceptions-examining-exception-contents.md)

- [Exceptions : Libération d’objets dans les exceptions](../mfc/exceptions-freeing-objects-in-exceptions.md)

- [Exceptions : Levée d’exceptions à partir de vos propres fonctions](../mfc/exceptions-throwing-exceptions-from-your-own-functions.md)

- [Exceptions : Exceptions de base de données](../mfc/exceptions-database-exceptions.md)

- [Exceptions : Exceptions OLE](../mfc/exceptions-ole-exceptions.md)

Les articles suivants comparent les macros d’exceptions MFC C++ avec les mots clés d’exception et expliquent comment adapter votre code:

- [Exceptions : Modifications apportées aux macros d’exception dans la version 3.0](../mfc/exceptions-changes-to-exception-macros-in-version-3-0.md)

- [Exceptions : Conversion à partir de macros d’exception MFC](../mfc/exceptions-converting-from-mfc-exception-macros.md)

- [Exceptions : Utilisation de macros MFC et d’exceptions C++](../mfc/exceptions-using-mfc-macros-and-cpp-exceptions.md)

## <a name="see-also"></a>Voir aussi

[Gestion d’exceptions C++](../cpp/cpp-exception-handling.md)<br/>
[Comment faire: Créer mes propres classes d’exceptions personnalisées](https://go.microsoft.com/fwlink/p/?linkid=128045)
