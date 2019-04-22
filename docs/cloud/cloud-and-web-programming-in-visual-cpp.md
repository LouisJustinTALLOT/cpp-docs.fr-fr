---
title: Cloud et programmation Web dans Visual C++
ms.date: 11/04/2016
ms.assetid: b63611f1-9723-44d0-ba7f-c3ebef341313
ms.openlocfilehash: 33431a8f8660af683ed2e39e10811c22fe2f4fcc
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58773084"
---
# <a name="cloud-and-web-programming-in-visual-c"></a>Cloud et programmation Web dans Visual C++

En C++, vous disposez de plusieurs options de connexion web et cloud.

## <a name="cloud-programming-options"></a>Options de programmation de cloud

- [Microsoft Azure Mobile Services](http://www.windowsazure.com/develop/mobile/)

  Fournit des API natives que vous pouvez utiliser dans les applications de plateforme universelle Windows (UWP) ou des applications de bureau Windows pour se connecter à Windows Azure Mobile Services. Bien que la plupart des exemples présentés sur le site web soient en C#, vous pouvez aussi utiliser C++. Pour plus d’informations, consultez [Démarrage rapide : Ajout d’un service mobile à l’aide de C++](https://msdn.microsoft.com/library/windows/apps/dn263181.aspx).

- [Bibliothèque cliente de stockage Microsoft Azure pour C++](https://blogs.msdn.microsoft.com/windowsazurestorage/2015/04/29/microsoft-azure-storage-client-library-for-c-v1-0-0-general-availability/)

  La bibliothèque de Client de stockage Azure pour C++ fournit une API complète pour travailler avec le stockage Azure, y compris de manière non limitative, les possibilités suivantes :

  - Créer, lire, supprimer et répertorier les conteneurs d’objets blob, tables et files d’attente.
  - Créer, lire, supprimer, liste et copie les objets BLOB plus lire et écrire des plages d’objets blob.
  - INSERT, delete, replace, fusion et interroger des entités dans une table Azure.
  - File d’attente et la file d’attente de messages dans une file d’attente Azure.
  - Liste tardivement des conteneurs, objets BLOB, tables et files d’attente et interroger en différé des entités

- [API OneDrive](https://dev.onedrive.com/README.htm)

  L’API OneDrive fournit un ensemble de services HTTP pour connecter votre application aux fichiers et dossiers dans Office 365 et SharePoint Server 2016.

- [SDK C++ REST (nom de code Casablanca)](https://github.com/Microsoft/cpprestsdk)

  Fournit une API moderne, multiplateforme et asynchrone permettant d’interagir avec les services REST.

  - Effectuer des appels REST par rapport à n’importe quel serveur HTTP, avec prise en charge intégrée pour la sérialisation et de l’analyse de documents JSON
  - Prend en charge OAuth 1 et 2, y compris un écouteur local de redirection
  - Établir des connexions WebSocket par rapport à des services à distance
  - Une tâche asynchrone entièrement API basée sur la bibliothèque PPL, y compris un pool de threads intégré

  Prend en charge de Windows Desktop (7 +), Windows Server (2012 et versions ultérieures), plateforme Windows universelle, Linux, OSX, Android et iOS.

- [Windows::Web::Http::HttpClient](/uwp/api/windows.web.http.httpclient)

  Classe de client HTTP Windows Runtime modélisée sur la classe .NET Framework du même nom dans l'espace de noms System.Web. `HttpClient` prend entièrement en charge le chargement et le téléchargement asynchrones via HTTP, ainsi que les filtres de pipeline qui permettent l'insertion de gestionnaires HTTP personnalisés dans le pipeline. Le Kit de développement logiciel (SDK) Windows inclut des exemples de filtres pour les connexions réseau limitées, l'authentification OAuth et bien plus encore. Pour les applications qui ciblent uniquement les plateforme Windows universelle, nous vous recommandons d’utiliser la `Windows::Web:HttpClient` classe.

- [Interface IXMLHTTPRequest2](/windows/desktop/api/msxml6/nn-msxml6-ixmlhttprequest2)

  Fournit une interface COM native que vous pouvez utiliser dans les applications Windows Runtime ou des applications de bureau Windows pour se connecter à Internet via HTTP et émettre GET, PUT et d’autres commandes HTTP. Pour plus d’informations, consultez [Procédure pas à pas : Connexion à l’aide de tâches et les requêtes HTTP XML](../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md).

- [Windows Internet (WinInet)](/windows/desktop/WinInet/portal)

  API Windows que vous pouvez utiliser dans les applications de bureau Windows pour vous connecter à Internet.

## <a name="see-also"></a>Voir aussi

[Visual C++](../overview/visual-cpp-in-visual-studio.md) <br/>
[Réseaux et services web](/windows/uwp/networking/)
