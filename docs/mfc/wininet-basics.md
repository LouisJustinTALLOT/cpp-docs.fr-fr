---
title: Éléments fondamentaux relatifs à WinInet
ms.date: 11/04/2016
helpviewer_keywords:
- OnStatusCallback method [MFC]
- WinInet classes [MFC], displaying progress
- WinInet classes [MFC], about WinInet classes
ms.assetid: 665de5ac-e80d-427d-8d91-2ae466885940
ms.openlocfilehash: b989e5c3df63ee7b5129d01468a0f869772ed286
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367323"
---
# <a name="wininet-basics"></a>Éléments fondamentaux relatifs à WinInet

Vous pouvez utiliser WinInet pour ajouter le support FTP pour télécharger et télécharger des fichiers à partir de votre application. Vous pouvez remplacer [OnStatusCallback](../mfc/reference/cinternetsession-class.md#onstatuscallback) et utiliser le paramètre *dwContext* pour fournir des informations de progression aux utilisateurs que vous recherchez et téléchargez des fichiers.

Cet article contient les sujets suivants:

- [Créer un navigateur très simple](#_core_create_a_very_simple_browser)

- [Télécharger une page Web](#_core_download_a_web_page)

- [FTP un fichier](#_core_ftp_a_file)

- [Récupérer un répertoire Gopher](#_core_retrieve_a_gopher_directory)

- [Afficher les informations sur les progrès lors du transfert de fichiers](#_core_display_progress_information_while_transferring_files)

Les extraits de code ci-dessous montrent comment créer un navigateur simple, télécharger une page Web, FTP un fichier, et rechercher un fichier gopher. Ils ne sont pas destinés à être des exemples complets et ne contiennent pas tous de la manipulation des exceptions.

Pour plus d’informations sur WinInet, voir [Win32 Internet Extensions (WinInet)](../mfc/win32-internet-extensions-wininet.md).

## <a name="create-a-very-simple-browser"></a><a name="_core_create_a_very_simple_browser"></a>Créer un navigateur très simple

[!code-cpp[NVC_MFCWinInet#1](../mfc/codesnippet/cpp/wininet-basics_1.cpp)]

## <a name="download-a-web-page"></a><a name="_core_download_a_web_page"></a>Télécharger une page Web

[!code-cpp[NVC_MFCWinInet#2](../mfc/codesnippet/cpp/wininet-basics_2.cpp)]

## <a name="ftp-a-file"></a><a name="_core_ftp_a_file"></a>FTP un fichier

[!code-cpp[NVC_MFCWinInet#3](../mfc/codesnippet/cpp/wininet-basics_3.cpp)]

## <a name="retrieve-a-gopher-directory"></a><a name="_core_retrieve_a_gopher_directory"></a>Récupérer un répertoire Gopher

[!code-cpp[NVC_MFCWinInet#4](../mfc/codesnippet/cpp/wininet-basics_4.cpp)]

## <a name="use-onstatuscallback"></a>Utiliser OnStatusCallback

Lorsque vous utilisez les classes WinInet, vous pouvez utiliser le membre [OnStatusCallback](../mfc/reference/cinternetsession-class.md#onstatuscallback) de l’objet [CInternetSession](../mfc/reference/cinternetsession-class.md) de votre application pour récupérer les informations d’état. Si vous dérivez votre `CInternetSession` `OnStatusCallback`propre objet, remplacez et activez `OnStatusCallback` les rappels de statut, MFC appellera votre fonction avec des informations de progrès sur toutes les activités de cette session Internet.

Étant donné qu’une seule session peut prendre en charge plusieurs `OnStatusCallback` connexions (qui, au cours de leur vie, peuvent effectuer de nombreuses opérations distinctes différentes), a besoin d’un mécanisme pour identifier chaque changement de statut avec une connexion ou une transaction particulière. Ce mécanisme est fourni par le paramètre d’identification contextuelle donné à bon nombre des fonctions des membres dans les classes de soutien WinInet. Ce paramètre est toujours de type **DWORD** et est toujours nommé *dwContext*.

Le contexte assigné à un objet Internet particulier n’est `OnStatusCallback` utilisé que `CInternetSession` pour identifier l’activité que l’objet provoque dans le membre de l’objet. L’appel `OnStatusCallback` à recevoir plusieurs paramètres; ces paramètres travaillent ensemble pour indiquer à votre application quels progrès ont été réalisés pour quelle transaction et connexion.

Lorsque vous `CInternetSession` créez un objet, vous pouvez spécifier un paramètre *dwContext* au constructeur. `CInternetSession`lui-même n’utilise pas l’ID contexte; au lieu de cela, il transmet l’ID de contexte à tous les objets dérivés **d’InternetConnection**qui n’obtiennent pas explicitement un ID de contexte de leur propre. À leur `CInternetConnection` tour, ces objets transmettront `CInternetFile` l’ID contextuelle aux objets qu’ils créent si vous ne spécifiez pas explicitement un ID de contexte différent. Si, d’autre part, vous spécifiez une pièce d’identité de contexte spécifique de votre propre, l’objet et tout travail qu’il fait sera associé à cette ID contexte. Vous pouvez utiliser les identifications contextuelles pour identifier les `OnStatusCallback` informations de statut qui vous sont données dans votre fonction.

## <a name="display-progress-information-while-transferring-files"></a><a name="_core_display_progress_information_while_transferring_files"></a>Afficher les informations sur les progrès lors du transfert de fichiers

Par exemple, si vous écrivez une application qui crée une connexion avec un serveur FTP pour lire un fichier `CInternetSession` et `CInternetConnection` se connecte également `CFtpSession` à un serveur `CHttpSession`HTTP pour obtenir une page Web, vous aurez un objet, deux objets (l’un serait un et l’autre serait un ), et deux `CInternetFile` objets (un pour chaque connexion). Si vous avez utilisé des valeurs par défaut pour les paramètres *dwContext,* vous ne seriez pas en mesure de faire la distinction entre les invocations qui indiquent les `OnStatusCallback` progrès pour la connexion FTP et les invocations qui indiquent des progrès pour la connexion HTTP. Si vous spécifiez un *ID dwContext,* que vous pouvez tester plus tard, `OnStatusCallback`vous saurez quelle opération a généré le rappel.

## <a name="see-also"></a>Voir aussi

[MFC Internet Programming Basics](../mfc/mfc-internet-programming-basics.md)<br/>
[Extension Internet Win32 (WinInet)](../mfc/win32-internet-extensions-wininet.md)
