---
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
ms.openlocfilehash: d339ec98dabc6cb24fc7106c4c7238cd6a14a71b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365537"
---
# <a name="exception-handling-in-mfc"></a>Gestion des exceptions dans MFC

Cet article explique les mécanismes de manipulation des exceptions disponibles dans MFC. Deux mécanismes sont disponibles :

- Exceptions CMD, disponibles dans la version MFC 3.0 et plus tard

- Les macros d’exception MFC, disponibles dans les versions MFC 1.0 et plus tard

Si vous écrivez une nouvelle application à l’aide de MFC, vous devez utiliser le mécanisme CMD. Vous pouvez utiliser le mécanisme macro-basé si votre application existante utilise déjà ce mécanisme en profondeur.

Vous pouvez facilement convertir le code existant pour utiliser les exceptions C au lieu des macros d’exception MFC. Les avantages de la conversion de votre code et des lignes directrices pour ce faire sont décrits dans l’article [Exceptions: Conversion de MFC Exception Macros](../mfc/exceptions-converting-from-mfc-exception-macros.md).

Si vous avez déjà développé une application à l’aide des macros d’exception MFC, vous pouvez continuer à utiliser ces macros dans votre code existant, tout en utilisant des exceptions CMD dans votre nouveau code. L’article [Exceptions: Changes to Exception Macros in Version 3.0](../mfc/exceptions-changes-to-exception-macros-in-version-3-0.md) donne des lignes directrices pour ce faire.

> [!NOTE]
> Pour activer la gestion des exceptions CMD dans votre code, sélectionnez Les exceptions Enable CMD sur la page Génération de Code dans le dossier C/CMD de la boîte de dialogue [des Pages de propriété](../build/reference/property-pages-visual-cpp.md) du projet, ou utilisez l’option compilateur [/EHsc.](../build/reference/eh-exception-handling-model.md)

Cet article aborde les thèmes suivants :

- [quand utiliser les exceptions](#_core_when_to_use_exceptions)

- [Soutien aux exceptions MFC](#_core_mfc_exception_support)

- [Lire plus loin sur les exceptions](#_core_further_reading_about_exceptions)

## <a name="when-to-use-exceptions"></a><a name="_core_when_to_use_exceptions"></a>Quand utiliser les exceptions

Trois catégories de résultats peuvent se produire lorsqu’une fonction est appelée pendant l’exécution du programme : exécution normale, exécution erronée ou exécution anormale. Chaque catégorie est décrite ci-dessous.

- Exécution normale

   La fonction peut s’exécuter normalement et revenir. Certaines fonctions renvoient un code de résultat à l’appelant, ce qui indique le résultat de la fonction. Les codes de résultat possibles sont strictement définis pour la fonction et représentent l’éventail des résultats possibles de la fonction. Le code de résultat peut indiquer le succès ou l’échec ou peut même indiquer un type particulier d’échec qui se situe dans la plage normale d’attentes. Par exemple, une fonction d’état de fichier peut retourner un code qui indique que le fichier n’existe pas. Notez que le terme « code d’erreur » n’est pas utilisé parce qu’un code de résultat représente l’un des nombreux résultats attendus.

- Exécution erronée

   L’appelant fait une erreur en passant des arguments à la fonction ou appelle la fonction dans un contexte inapproprié. Cette situation provoque une erreur, et elle doit être détectée par une affirmation au cours de l’élaboration du programme. (Pour plus d’informations sur les affirmations, voir [affirmations C/C.)](/visualstudio/debugger/c-cpp-assertions)

- Exécution anormale

   L’exécution anormale comprend des situations où des conditions en dehors du contrôle du programme, telles que des erreurs de mémoire ou d’I/O, influencent le résultat de la fonction. Les situations anormales doivent être traitées en attrapant et en lançant des exceptions.

L’utilisation d’exceptions est particulièrement appropriée pour l’exécution anormale.

## <a name="mfc-exception-support"></a><a name="_core_mfc_exception_support"></a>Soutien aux exceptions MFC

Que vous utilisiez directement les exceptions CMD ou que vous utilisiez les macros d’exception MFC, vous utiliserez [la classe CException](../mfc/reference/cexception-class.md) ou `CException`des objets dérivés qui peuvent être jetés par le cadre ou par votre application.

Le tableau suivant montre les exceptions prédéfinie fournies par MFC.

|Exception (classe)|Signification|
|---------------------|-------------|
|[Classe CMemoryException](../mfc/reference/cmemoryexception-class.md)|Hors mémoire|
|[CFileException, classe](../mfc/reference/cfileexception-class.md)|Exception de fichier|
|[CArchiveException, classe](../mfc/reference/carchiveexception-class.md)|Exception Archives/Serialisation|
|[Classe D’origine CNotSupportedException](../mfc/reference/cnotsupportedexception-class.md)|Réponse à la demande de service non pris en service|
|[Classe CResourceException](../mfc/reference/cresourceexception-class.md)|Exception sur l’allocation des ressources Windows|
|[Classe CDaoException](../mfc/reference/cdaoexception-class.md)|Exceptions de base de données (classes DAO)|
|[CDBException, classe](../mfc/reference/cdbexception-class.md)|Exceptions aux bases de données (classes ODBC)|
|[Classe COleException](../mfc/reference/coleexception-class.md)|exceptions OLE|
|[COleDispatchException, classe](../mfc/reference/coledispatchexception-class.md)|Exceptions d’expédition (automatisation)|
|[CUserException, classe](../mfc/reference/cuserexception-class.md)|Exception qui alerte l’utilisateur avec une boîte de message, puis lance une [classe CException](../mfc/reference/cexception-class.md) générique|

Depuis la version 3.0, MFC utilise des exceptions C++ mais prend toujours en charge les macros plus anciennes de gestion des exceptions, qui sont similaires aux exceptions C++ en termes de format. Bien que ces macros ne soient pas recommandées pour une nouvelle programmation, elles sont toujours prises en charge pour la compatibilité descendante. Dans les programmes qui utilisent déjà les macros, vous pouvez également utiliser des exceptions C++. Pendant le prétraitement, les macros évaluent les mots clés de manutention d’exception définis dans la mise en œuvre MSVC de la langue CMD à partir de la version 2.0 visualiseur. Vous pouvez laisser les macros des exceptions existantes telles qu'elles sont lorsque vous commencez à utiliser des exceptions C++. Pour plus d’informations sur le mélange des macros et de la manipulation des exceptions C ET sur la conversion de l’ancien code pour utiliser le nouveau mécanisme, voir les articles [Exceptions: Utilisation de macros MFC et C 'Exceptions](../mfc/exceptions-using-mfc-macros-and-cpp-exceptions.md) et [Exceptions: Convertir de MFC Exception Macros](../mfc/exceptions-converting-from-mfc-exception-macros.md). Les anciennes macros d'exceptions MFC, si vous les utilisez toujours, correspondent aux mots clés d'exception C++. Voir [Exceptions: Changements aux macros d’exception dans la version 3.0](../mfc/exceptions-changes-to-exception-macros-in-version-3-0.md). MFC ne prend pas directement en charge windows NT gestionnaires d’exception structurés (SEH), comme discuté dans [Structured Exception Handling](/windows/win32/debug/structured-exception-handling).

## <a name="further-reading-about-exceptions"></a><a name="_core_further_reading_about_exceptions"></a>Lire plus loin sur les exceptions

Les articles suivants expliquent l’utilisation de la bibliothèque MFC pour la remise d’exception :

- [Exceptions : interception et suppression d’exceptions](../mfc/exceptions-catching-and-deleting-exceptions.md)

- [Exceptions : examen du contenu des exceptions](../mfc/exceptions-examining-exception-contents.md)

- [Exceptions : libération d'objets dans les exceptions](../mfc/exceptions-freeing-objects-in-exceptions.md)

- [Exceptions : levée d'exceptions à partir de vos propres fonctions](../mfc/exceptions-throwing-exceptions-from-your-own-functions.md)

- [Exceptions : exceptions de base de données](../mfc/exceptions-database-exceptions.md)

- [Exceptions : exceptions OLE](../mfc/exceptions-ole-exceptions.md)

Les articles suivants comparent les macros d’exception MFC avec les mots clés d’exception CMD et expliquent comment vous pouvez adapter votre code :

- [Exceptions : modifications apportées aux macros d'exception dans la version 3.0](../mfc/exceptions-changes-to-exception-macros-in-version-3-0.md)

- [Exceptions : conversion à partir de macros d'exception MFC](../mfc/exceptions-converting-from-mfc-exception-macros.md)

- [Exceptions : utilisation de macros MFC et d’exceptions C++](../mfc/exceptions-using-mfc-macros-and-cpp-exceptions.md)

## <a name="see-also"></a>Voir aussi

[Pratiques exemplaires modernes de CMD pour les exceptions et le traitement des erreurs](../cpp/errors-and-exception-handling-modern-cpp.md)<br/>
[Comment puis-je : Créer mes propres classes d’exception personnalisées](https://go.microsoft.com/fwlink/p/?linkid=128045)
