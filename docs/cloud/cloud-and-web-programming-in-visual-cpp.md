---
title: Cloud et programmation Web dans Visual C++
ms.date: 11/04/2016
ms.assetid: b63611f1-9723-44d0-ba7f-c3ebef341313
ms.openlocfilehash: 3d71e36b6209c693940f2ebe6b5e9c73bc0c9d9d
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65708045"
---
# <a name="cloud-and-web-programming-in-visual-c"></a>Cloud et programmation Web dans Visual C++

En C++, vous disposez de plusieurs options de connexion web et cloud.

## <a name="cloud-programming-options"></a>Options de programmation cloud

- [Microsoft Azure Mobile Services](http://www.windowsazure.com/develop/mobile/)

  Fournit des API natives que vous pouvez utiliser dans les applications UWP ou Windows Desktop pour vous connecter à Microsoft Azure Mobile Services. Bien que la plupart des exemples présentés sur le site web soient en C#, vous pouvez aussi utiliser C++. Pour plus d’informations, consultez [Démarrage rapide : Ajout d’un service mobile avec C++](https://msdn.microsoft.com/library/windows/apps/dn263181.aspx).

- [Microsoft Azure Storage Client Library for C++](https://blogs.msdn.microsoft.com/windowsazurestorage/2015/04/29/microsoft-azure-storage-client-library-for-c-v1-0-0-general-availability/)

  La bibliothèque cliente Stockage Azure pour C++ fournit une API complète pour l’utilisation de Stockage Azure, avec notamment les possibilités suivantes :

  - Créer, lire, supprimer et lister des conteneurs d’objets blob, des tables et des files d’attente.
  - Créer, lire, supprimer, lister et copier les objets blob, et lire et écrire des plages d’objets blob.
  - Insérer, supprimer, remplacer, fusionner et interroger des entités dans une table Azure.
  - Placer et extraire des messages dans une file d’attente Azure.
  - Lister en différé des conteneurs, des objets blob, des tables et des files d’attente, et interroger en différé des entités

- [API OneDrive](https://dev.onedrive.com/README.htm)

  L’API OneDrive fournit un ensemble de services HTTP pour connecter votre application à des fichiers et des dossiers dans Office 365 et SharePoint Server 2016.

- [SDK C++ REST (nom de code Casablanca)](https://github.com/Microsoft/cpprestsdk)

  Fournit une API moderne, multiplateforme et asynchrone permettant d’interagir avec les services REST.

  - Effectuer des appels REST auprès de n’importe quel serveur HTTP, avec une prise en charge intégrée de l’analyse et de la sérialisation de documents JSON
  - Prend en charge OAuth 1 et 2, avec notamment un écouteur de redirection local
  - Établir des connexions WebSocket avec des services distants
  - Une API de tâches entièrement asynchrones basée sur PPL, avec notamment un pool de threads intégré

  Prend en charge Windows Desktop (7+), Windows Server (2012+), UWP, Linux, OSX, Android et iOS.

- [Windows::Web::Http::HttpClient](/uwp/api/windows.web.http.httpclient)

  Classe de client HTTP Windows Runtime modélisée sur la classe .NET Framework du même nom dans l'espace de noms System.Web. `HttpClient` prend entièrement en charge le chargement et le téléchargement asynchrones via HTTP, ainsi que les filtres de pipeline qui permettent l'insertion de gestionnaires HTTP personnalisés dans le pipeline. Le Kit de développement logiciel (SDK) Windows inclut des exemples de filtres pour les connexions réseau limitées, l'authentification OAuth et bien plus encore. Pour les applications qui ciblent seulement UWP, nous vous recommandons d’utiliser la classe `Windows::Web:HttpClient`.

- [Interface IXMLHTTPRequest2](/windows/desktop/api/msxml6/nn-msxml6-ixmlhttprequest2)

  Fournit une interface COM native que vous pouvez utiliser dans les applications Windows Runtime ou les applications Windows Desktop pour vous connecter à Internet via HTTP, et émettre des commandes GET et PUT, et d’autres commandes HTTP. Pour plus d’informations, consultez [Procédure pas à pas : Connexion à l’aide de tâches et de requêtes HTTP XML](../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md).

- [Windows Internet (WinInet)](/windows/desktop/WinInet/portal)

  API Windows que vous pouvez utiliser dans les applications de bureau Windows pour vous connecter à Internet.

## <a name="see-also"></a>Voir aussi

[C++ dans Visual Studio](../overview/visual-cpp-in-visual-studio.md) <br/>
[Réseaux et services web](/windows/uwp/networking/)
