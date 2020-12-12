---
description: 'En savoir plus sur : concepts de base de WinInet'
title: Éléments fondamentaux relatifs à WinInet
ms.date: 11/04/2016
helpviewer_keywords:
- OnStatusCallback method [MFC]
- WinInet classes [MFC], displaying progress
- WinInet classes [MFC], about WinInet classes
ms.assetid: 665de5ac-e80d-427d-8d91-2ae466885940
ms.openlocfilehash: 1ba8f9b898476849ca9bbb39b7850bbce3605154
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97172776"
---
# <a name="wininet-basics"></a>Éléments fondamentaux relatifs à WinInet

Vous pouvez utiliser WinInet pour ajouter la prise en charge FTP pour télécharger et charger des fichiers à partir de votre application. Vous pouvez remplacer [OnStatusCallback](../mfc/reference/cinternetsession-class.md#onstatuscallback) et utiliser le paramètre *dwContext* pour fournir des informations de progression aux utilisateurs lors de la recherche et du téléchargement de fichiers.

Cet article contient les rubriques suivantes :

- [Créer un navigateur très simple](#_core_create_a_very_simple_browser)

- [Télécharger une page Web](#_core_download_a_web_page)

- [FTP un fichier](#_core_ftp_a_file)

- [Récupérer un répertoire Gopher](#_core_retrieve_a_gopher_directory)

- [Afficher les informations de progression lors du transfert de fichiers](#_core_display_progress_information_while_transferring_files)

Les extraits de code ci-dessous montrent comment créer un navigateur simple, télécharger une page Web, FTP un fichier et Rechercher un fichier Gopher. Elles ne sont pas des exemples complets et ne contiennent pas toutes la gestion des exceptions.

Pour plus d’informations sur WinInet, consultez [extensions Internet Win32 (WinInet)](../mfc/win32-internet-extensions-wininet.md).

## <a name="create-a-very-simple-browser"></a><a name="_core_create_a_very_simple_browser"></a> Créer un navigateur très simple

[!code-cpp[NVC_MFCWinInet#1](../mfc/codesnippet/cpp/wininet-basics_1.cpp)]

## <a name="download-a-web-page"></a><a name="_core_download_a_web_page"></a> Télécharger une page Web

[!code-cpp[NVC_MFCWinInet#2](../mfc/codesnippet/cpp/wininet-basics_2.cpp)]

## <a name="ftp-a-file"></a><a name="_core_ftp_a_file"></a> FTP un fichier

[!code-cpp[NVC_MFCWinInet#3](../mfc/codesnippet/cpp/wininet-basics_3.cpp)]

## <a name="retrieve-a-gopher-directory"></a><a name="_core_retrieve_a_gopher_directory"></a> Récupérer un répertoire Gopher

[!code-cpp[NVC_MFCWinInet#4](../mfc/codesnippet/cpp/wininet-basics_4.cpp)]

## <a name="use-onstatuscallback"></a>Utiliser OnStatusCallback

Lorsque vous utilisez les classes WinInet, vous pouvez utiliser le membre [OnStatusCallback](../mfc/reference/cinternetsession-class.md#onstatuscallback) de l’objet [CInternetSession](../mfc/reference/cinternetsession-class.md) de votre application pour récupérer les informations d’État. Si vous dérivez votre propre `CInternetSession` objet, substituez `OnStatusCallback` et activez les rappels d’État, MFC appellera votre `OnStatusCallback` fonction avec des informations de progression sur l’ensemble de l’activité de cette session Internet.

Étant donné qu’une seule session peut prendre en charge plusieurs connexions (qui, pendant leur durée de vie, peuvent effectuer de nombreuses opérations distinctes), `OnStatusCallback` a besoin d’un mécanisme pour identifier chaque modification d’État avec une connexion ou une transaction particulière. Ce mécanisme est fourni par le paramètre d’ID de contexte donné à la plupart des fonctions membres dans les classes de prise en charge WinInet. Ce paramètre est toujours de type **DWORD** et est toujours nommé *dwContext*.

Le contexte affecté à un objet Internet particulier est utilisé uniquement pour identifier l’activité que l’objet entraîne dans le `OnStatusCallback` membre de l' `CInternetSession` objet. L’appel à `OnStatusCallback` reçoit plusieurs paramètres ; ces paramètres fonctionnent ensemble pour indiquer à votre application la progression de la transaction et de la connexion.

Lorsque vous créez un `CInternetSession` objet, vous pouvez spécifier un paramètre *dwContext* pour le constructeur. `CInternetSession` elle-même n’utilise pas l’ID de contexte ; au lieu de cela, elle passe l’ID de contexte à tous les objets dérivés de **InternetConnection** qui n’obtiennent pas explicitement un ID de contexte propre. À leur tour, ces `CInternetConnection` objets transmettent l’ID de contexte aux `CInternetFile` objets qu’ils créent si vous ne spécifiez pas explicitement un ID de contexte différent. Si, en revanche, vous spécifiez un ID de contexte spécifique, l’objet et tout travail qu’il contient seront associés à cet ID de contexte. Vous pouvez utiliser les ID de contexte pour identifier les informations d’État qui vous sont fournies dans votre `OnStatusCallback` fonction.

## <a name="display-progress-information-while-transferring-files"></a><a name="_core_display_progress_information_while_transferring_files"></a> Afficher les informations de progression lors du transfert de fichiers

Par exemple, si vous écrivez une application qui crée une connexion avec un serveur FTP pour lire un fichier et se connecte également à un serveur HTTP pour obtenir une page Web, vous disposez d’un `CInternetSession` objet, de deux objets (l’un est un `CInternetConnection` `CFtpSession` et l’autre est un `CHttpSession` ) et de deux `CInternetFile` objets (un pour chaque connexion). Si vous avez utilisé des valeurs par défaut pour les paramètres *dwContext* , vous ne pouvez pas faire la distinction entre les `OnStatusCallback` appels qui indiquent la progression de la connexion FTP et les appels qui indiquent la progression de la connexion http. Si vous spécifiez un ID *dwContext* , que vous pouvez ensuite tester ultérieurement dans `OnStatusCallback` , vous saurez quelle opération a généré le rappel.

## <a name="see-also"></a>Voir aussi

[Concepts de base de la programmation Internet MFC](../mfc/mfc-internet-programming-basics.md)<br/>
[Extensions Internet Win32 (WinInet)](../mfc/win32-internet-extensions-wininet.md)
