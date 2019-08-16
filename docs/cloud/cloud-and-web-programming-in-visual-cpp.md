---
title: Cloud et programmation Web dans Visual C++
ms.date: 05/14/2019
ms.assetid: b63611f1-9723-44d0-ba7f-c3ebef341313
ms.openlocfilehash: 3f4786d8b17aed2d7faeddf1e2c32a825fd8d0e5
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69498870"
---
# <a name="cloud-and-web-programming-in-visual-c"></a>Cloud et programmation Web dans Visual C++

En C++, vous disposez de plusieurs options de connexion web et cloud.

## <a name="microsoft-azure-sdks-and-rest-services"></a>Services REST et Kits de développement logiciel (SDK) Microsoft Azure

- [Bibliothèque cliente Stockage Microsoft Azure pour C++](https://azure.github.io/azure-storage-cpp/)

  La bibliothèque cliente Stockage Azure pour C++ fournit une API complète pour l’utilisation de Stockage Azure, avec notamment les possibilités suivantes :

  - Créer, lire, supprimer et lister des conteneurs d’objets blob, des tables et des files d’attente.
  - Créer, lire, supprimer, lister et copier les objets blob, et lire et écrire des plages d’objets blob.
  - Insérer, supprimer, remplacer, fusionner et interroger des entités dans une table Azure.
  - Placer et extraire des messages dans une file d’attente Azure.
  - Lister en différé des conteneurs, des objets blob, des tables et des files d’attente, et interroger en différé des entités

- La norme ANSI C99 [Kits de développement logiciel (SDK) Azure IoT Hub](/azure/iot-hub/iot-hub-devguide-sdks) concernant l’Internet des objets autorise les applications IoT à s’exécuter sur l’appareil ou sur le serveur principal.

- [OneDrive et SharePoint dans Microsoft Graph](https://dev.onedrive.com/README.htm)

  L’API OneDrive fournit un ensemble de services HTTP pour connecter votre application à des fichiers et des dossiers dans Office 365 et SharePoint Server 2016.

## <a name="windows-and-cross-platform-networking-apis"></a>API réseau Windows et multiplateformes

- [Kit de développement logiciel (SDK) C++ REST (nom de code Casablanca)](https://github.com/Microsoft/cpprestsdk)

  Fournit une API moderne, multiplateforme et asynchrone permettant d’interagir avec les services REST.

  - Effectuer des appels REST auprès de n’importe quel serveur HTTP, avec une prise en charge intégrée de l’analyse et de la sérialisation de documents JSON
  - Prend en charge OAuth 1 et 2, avec notamment un écouteur de redirection local
  - Établir des connexions WebSocket avec des services distants
  - Une API de tâches entièrement asynchrones basée sur PPL, avec notamment un pool de threads intégré

  Prend en charge Windows Desktop (7+), Windows Server (2012+), UWP, Linux, OSX, Android et iOS.

- [Windows::Web::Http::HttpClient](/uwp/api/windows.web.http.httpclient)

  Classe de client HTTP Windows Runtime modélisée sur la classe .NET Framework du même nom dans l'espace de noms System.Web. `HttpClient` prend entièrement en charge le chargement et le téléchargement asynchrones via HTTP, ainsi que les filtres de pipeline qui permettent l'insertion de gestionnaires HTTP personnalisés dans le pipeline. Le Kit de développement logiciel (SDK) Windows inclut des exemples de filtres pour les connexions réseau limitées, l'authentification OAuth et bien plus encore. Pour les applications qui ciblent seulement UWP, nous vous recommandons d’utiliser la classe `Windows::Web:HttpClient`.

- [Interface IXMLHTTPRequest2](/windows/win32/api/msxml6/nn-msxml6-ixmlhttprequest2)

  Fournit une interface COM native que vous pouvez utiliser dans les applications Windows Runtime ou les applications Windows Desktop pour vous connecter à Internet via HTTP, et émettre des commandes GET et PUT, et d’autres commandes HTTP. Pour plus d’informations, consultez [Procédure pas à pas : Connexion à l’aide de tâches et de requêtes HTTP XML](../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md).

- [Windows Internet (WinInet)](/windows/win32/WinInet/portal)

  API Windows que vous pouvez utiliser dans les applications de bureau Windows pour vous connecter à Internet.

## <a name="see-also"></a>Voir aussi

[C++ dans Visual Studio](../overview/visual-cpp-in-visual-studio.md) <br/>
[Centre de développement Microsoft Azure C et C++](https://azure.microsoft.com/develop/cpp/) <br/>
[Réseaux et services web (plateforme Windows universelle)](/windows/uwp/networking/)
