---
title: Éléments fondamentaux relatifs à WinInet
ms.date: 11/04/2016
helpviewer_keywords:
- OnStatusCallback method [MFC]
- WinInet classes [MFC], displaying progress
- WinInet classes [MFC], about WinInet classes
ms.assetid: 665de5ac-e80d-427d-8d91-2ae466885940
ms.openlocfilehash: 79ec102aa27440c64f03c6e22b9f2fe959cac6b9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62399549"
---
# <a name="wininet-basics"></a>Éléments fondamentaux relatifs à WinInet

Vous pouvez utiliser WinInet pour ajouter la prise en charge FTP pour télécharger et charger des fichiers à partir de votre application. Vous pouvez remplacer [OnStatusCallback](../mfc/reference/cinternetsession-class.md#onstatuscallback) et utiliser le *dwContext* paramètre pour fournir des informations de progression aux utilisateurs que vous recherchez et téléchargez des fichiers.

Cet article contient les rubriques suivantes :

- [Créer un navigateur très Simple](#_core_create_a_very_simple_browser)

- [Téléchargement d’une Page Web](#_core_download_a_web_page)

- [FTP d’un fichier](#_core_ftp_a_file)

- [Récupérer un répertoire Gopher](#_core_retrieve_a_gopher_directory)

- [Afficher les informations de progression lors du transfert de fichiers](#_core_display_progress_information_while_transferring_files)

Les extraits de code ci-dessous montrent comment créer un simple navigateur, télécharger une page Web, FTP, un fichier et rechercher un fichier gopher. N’est pas utilisé en tant que des exemples complets et contiennent pas toutes la gestion des exceptions.

Pour plus d’informations sur WinInet, consultez [extension Internet Win32 (WinInet)](../mfc/win32-internet-extensions-wininet.md).

##  <a name="_core_create_a_very_simple_browser"></a> Créer un navigateur très Simple

[!code-cpp[NVC_MFCWinInet#1](../mfc/codesnippet/cpp/wininet-basics_1.cpp)]

##  <a name="_core_download_a_web_page"></a> Téléchargement d’une Page Web

[!code-cpp[NVC_MFCWinInet#2](../mfc/codesnippet/cpp/wininet-basics_2.cpp)]

##  <a name="_core_ftp_a_file"></a> FTP d’un fichier

[!code-cpp[NVC_MFCWinInet#3](../mfc/codesnippet/cpp/wininet-basics_3.cpp)]

##  <a name="_core_retrieve_a_gopher_directory"></a> Récupérer un répertoire Gopher

[!code-cpp[NVC_MFCWinInet#4](../mfc/codesnippet/cpp/wininet-basics_4.cpp)]

## <a name="use-onstatuscallback"></a>Utilisation de OnStatusCallback

Lorsque vous utilisez les classes WinInet, vous pouvez utiliser la [OnStatusCallback](../mfc/reference/cinternetsession-class.md#onstatuscallback) membre de votre application [CInternetSession](../mfc/reference/cinternetsession-class.md) objet à récupérer les informations d’état. Si vous dérivez votre propre `CInternetSession` de l’objet, substituez `OnStatusCallback`et activer des rappels d’état, MFC appelle votre `OnStatusCallback` fonction avec des informations de progression sur toutes les activités de la session Internet.

Car une seule session peut prendre en charge plusieurs connexions (qui, pendant leur durée de vie, peuvent effectuer diverses opérations distinctes), `OnStatusCallback` a besoin d’un mécanisme pour identifier chaque changement d’état avec une connexion particulière ou d’une transaction. Ce mécanisme est fourni par le paramètre d’ID de contexte fourni à de nombreuses fonctions membres dans les classes de prise en charge de WinInet. Ce paramètre est toujours du type **DWORD** et est toujours nommé *dwContext*.

Le contexte affecté à un objet Internet particulier est utilisé uniquement pour identifier l’activité de l’objet provoque dans le `OnStatusCallback` membre de la `CInternetSession` objet. L’appel à `OnStatusCallback` reçoit plusieurs paramètres ; ces paramètres fonctionnent ensemble pour indiquer quels cours a été effectuée pour les transactions et la connexion à votre application.

Lorsque vous créez un `CInternetSession` objet, vous pouvez spécifier un *dwContext* paramètre au constructeur. `CInternetSession` lui-même n’utilise pas l’ID de contexte ; au lieu de cela, il passe l’ID de contexte avec l’un **InternetConnection**-objets qui ne reçoivent pas explicitement un ID de contexte de leur propre dérivés. À son tour, ceux `CInternetConnection` objets transmettra l’identificateur de contexte à `CInternetFile` objets qu’ils créent si vous ne spécifiez pas explicitement un ID de contexte différent. Si, en revanche, vous spécifiez un ID de contexte spécifique de votre choix, l’objet et n’importe quel travail qu’elle effectue sera associés à cet ID de contexte. Vous pouvez utiliser l’ID de contexte pour identifier les informations d’état sont fournies dans votre `OnStatusCallback` (fonction).

##  <a name="_core_display_progress_information_while_transferring_files"></a> Afficher les informations de progression lors du transfert de fichiers

Par exemple, si vous écrivez une application qui crée une connexion avec un serveur FTP pour lire un fichier et se connecte également à un serveur HTTP pour obtenir une page Web, vous aurez un `CInternetSession` objet, deux `CInternetConnection` objets (un serait un `CFtpSession` et l’autre serait un `CHttpSession`) et deux `CInternetFile` objets (un pour chaque connexion). Si vous avez utilisé les valeurs par défaut pour le *dwContext* paramètres, vous ne pourrez faire la distinction entre les `OnStatusCallback` appels qui indiquent la progression de la connexion FTP et les appels qui indiquent la progression de la Connexion HTTP. Si vous spécifiez un *dwContext* ID, que vous pouvez tester plus tard dans `OnStatusCallback`, vous saurez quels opération a généré le rappel.

## <a name="see-also"></a>Voir aussi

[Notions de base de la programmation Internet MFC](../mfc/mfc-internet-programming-basics.md)<br/>
[Extension Internet Win32 (WinInet)](../mfc/win32-internet-extensions-wininet.md)
