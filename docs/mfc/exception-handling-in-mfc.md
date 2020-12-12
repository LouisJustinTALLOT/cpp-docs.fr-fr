---
description: En savoir plus sur la gestion des exceptions dans MFC
title: Gestion des exceptions dans MFC
ms.date: 11/19/2019
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
ms.openlocfilehash: 15b0a054d3b1c0353c60c1c8dda03c9e704c077e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97290750"
---
# <a name="exception-handling-in-mfc"></a>Gestion des exceptions dans MFC

Cet article explique les mécanismes de gestion des exceptions disponibles dans MFC. Deux mécanismes sont disponibles :

- Exceptions C++, disponibles dans MFC version 3,0 et versions ultérieures

- Les macros d’exception MFC, disponibles dans les versions 1,0 et ultérieures de MFC

Si vous écrivez une nouvelle application à l’aide de MFC, vous devez utiliser le mécanisme C++. Vous pouvez utiliser le mécanisme basé sur les macros si votre application existante utilise déjà ce mécanisme de manière intensive.

Vous pouvez facilement convertir le code existant pour utiliser des exceptions C++ au lieu des macros d’exception MFC. Les avantages de la conversion de votre code et des directives pour ce faire sont décrits dans l’article [exceptions : conversion à partir de macros d’exception MFC](exceptions-converting-from-mfc-exception-macros.md).

Si vous avez déjà développé une application à l’aide des macros d’exception MFC, vous pouvez continuer à utiliser ces macros dans votre code existant, tout en utilisant des exceptions C++ dans votre nouveau code. L’article [exceptions : les modifications apportées aux macros d’exception dans la Version 3,0](exceptions-changes-to-exception-macros-in-version-3-0.md) fournissent des instructions pour ce faire.

> [!NOTE]
> Pour activer la gestion des exceptions C++ dans votre code, sélectionnez Activer les exceptions C++ sur la page génération de code dans le dossier C/C++ de la boîte de dialogue [pages de propriétés](../build/reference/property-pages-visual-cpp.md) du projet, ou utilisez l’option de compilateur [/EHsc](../build/reference/eh-exception-handling-model.md) .

Cet article aborde les thèmes suivants :

- [quand utiliser les exceptions](#_core_when_to_use_exceptions)

- [Prise en charge des exceptions MFC](#_core_mfc_exception_support)

- [En savoir plus sur les exceptions](#_core_further_reading_about_exceptions)

## <a name="when-to-use-exceptions"></a><a name="_core_when_to_use_exceptions"></a> Quand utiliser des exceptions

Trois catégories de résultats peuvent se produire lorsqu’une fonction est appelée pendant l’exécution du programme : exécution normale, exécution erronée ou exécution anormale. Chaque catégorie est décrite ci-dessous.

- Exécution normale

   La fonction peut s’exécuter normalement et retourner. Certaines fonctions retournent un code de résultat à l’appelant, ce qui indique le résultat de la fonction. Les codes de résultat possibles sont définis de façon stricte pour la fonction et représentent la plage des résultats possibles de la fonction. Le code de résultat peut indiquer la réussite ou l’échec ou peut même indiquer un type particulier de défaillance qui se trouve dans la plage normale des attentes. Par exemple, une fonction d’état de fichier peut retourner un code qui indique que le fichier n’existe pas. Notez que le terme « code d’erreur » n’est pas utilisé, car un code de résultat représente l’un des nombreux résultats attendus.

- Exécution erronée

   L’appelant fait une erreur lors du passage des arguments à la fonction ou appelle la fonction dans un contexte inapproprié. Cette situation provoque une erreur et doit être détectée par une assertion pendant le développement du programme. (Pour plus d’informations sur les assertions, consultez [assertions C/C++](/visualstudio/debugger/c-cpp-assertions).)

- Exécution anormale

   Une exécution anormale comprend des situations où des conditions en dehors du contrôle du programme, telles que de la mémoire insuffisante ou des erreurs d’e/s, influencent le résultat de la fonction. Les situations anormales doivent être gérées par l’interception et la levée d’exceptions.

L’utilisation d’exceptions est particulièrement appropriée pour une exécution anormale.

## <a name="mfc-exception-support"></a><a name="_core_mfc_exception_support"></a> Prise en charge des exceptions MFC

Que vous utilisiez les exceptions C++ directement ou que vous utilisiez les macros d’exception MFC, vous utiliserez la [classe CException](reference/cexception-class.md) ou les `CException` objets dérivés qui peuvent être levés par l’infrastructure ou par votre application.

Le tableau suivant présente les exceptions prédéfinies fournies par MFC.

|Exception (classe)|Signification|
|---------------------|-------------|
|[CMemoryException, classe](reference/cmemoryexception-class.md)|Mémoire insuffisante|
|[CFileException, classe](reference/cfileexception-class.md)|Exception de fichier|
|[CArchiveException, classe](reference/carchiveexception-class.md)|Exception d’archivage/sérialisation|
|[CNotSupportedException, classe](reference/cnotsupportedexception-class.md)|Réponse à la demande de service non pris en charge|
|[CResourceException, classe](reference/cresourceexception-class.md)|Exception d’allocation de ressources Windows|
|[CDaoException (classe)](reference/cdaoexception-class.md)|Exceptions de base de données (classes DAO)|
|[CDBException, classe](reference/cdbexception-class.md)|Exceptions de base de données (classes ODBC)|
|[COleException, classe](reference/coleexception-class.md)|exceptions OLE|
|[COleDispatchException, classe](reference/coledispatchexception-class.md)|Exceptions de dispatch (Automation)|
|[CUserException, classe](reference/cuserexception-class.md)|Exception qui avertit l’utilisateur avec une boîte de message, puis lève une [classe de CException](reference/cexception-class.md) générique|

Depuis la version 3.0, MFC utilise des exceptions C++ mais prend toujours en charge les macros plus anciennes de gestion des exceptions, qui sont similaires aux exceptions C++ en termes de format. Bien que ces macros ne soient pas recommandées pour une nouvelle programmation, elles sont toujours prises en charge pour la compatibilité descendante. Dans les programmes qui utilisent déjà les macros, vous pouvez également utiliser des exceptions C++. Pendant le prétraitement, les macros correspondent aux mots clés de gestion des exceptions définis dans l’implémentation MSVC du langage C++ à partir de Visual C++ version 2,0. Vous pouvez laisser les macros des exceptions existantes telles qu'elles sont lorsque vous commencez à utiliser des exceptions C++. Pour plus d’informations sur la combinaison de macros et de la gestion des exceptions C++ et sur la conversion d’un ancien code pour utiliser le nouveau mécanisme, consultez les articles [exceptions : utilisation de macros MFC et exceptions c++](exceptions-using-mfc-macros-and-cpp-exceptions.md) et [exceptions : conversion à partir de macros d’exceptions MFC](exceptions-converting-from-mfc-exception-macros.md). Les anciennes macros d'exceptions MFC, si vous les utilisez toujours, correspondent aux mots clés d'exception C++. Consultez [exceptions : modifications apportées aux macros d’exception dans la Version 3,0](exceptions-changes-to-exception-macros-in-version-3-0.md). MFC ne prend pas directement en charge les gestionnaires d’exceptions structurées (SEH) Windows NT, comme indiqué dans [gestion structurée des exceptions](/windows/win32/debug/structured-exception-handling).

## <a name="further-reading-about-exceptions"></a><a name="_core_further_reading_about_exceptions"></a> En savoir plus sur les exceptions

Les articles suivants expliquent comment utiliser la bibliothèque MFC pour la gestion des exceptions :

- [Exceptions : interception et suppression d’exceptions](exceptions-catching-and-deleting-exceptions.md)

- [Exceptions : examen du contenu des exceptions](exceptions-examining-exception-contents.md)

- [Exceptions : libération d’objets dans les exceptions](exceptions-freeing-objects-in-exceptions.md)

- [Exceptions : levée d’exceptions à partir de vos propres fonctions](exceptions-throwing-exceptions-from-your-own-functions.md)

- [Exceptions : exceptions de base de données](exceptions-database-exceptions.md)

- [Exceptions : exceptions OLE](exceptions-ole-exceptions.md)

Les articles suivants comparent les macros d’exceptions MFC avec les mots clés d’exception C++ et expliquent comment adapter votre code :

- [Exceptions : modifications apportées aux macros d’exception dans la version 3,0](exceptions-changes-to-exception-macros-in-version-3-0.md)

- [Exceptions : conversion à partir de macros d’exception MFC](exceptions-converting-from-mfc-exception-macros.md)

- [Exceptions : utilisation de macros MFC et d’exceptions C++](exceptions-using-mfc-macros-and-cpp-exceptions.md)

## <a name="see-also"></a>Voir aussi

[Meilleures pratiques C++ modernes pour les exceptions et la gestion des erreurs](../cpp/errors-and-exception-handling-modern-cpp.md)<br/>
[Comment faire : créer mes propres classes d’exceptions personnalisées](https://go.microsoft.com/fwlink/p/?linkid=128045)
