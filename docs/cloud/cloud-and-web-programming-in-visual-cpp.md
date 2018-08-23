---
title: Cloud et Web de programmation dans Visual C++ | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-azure
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: b63611f1-9723-44d0-ba7f-c3ebef341313
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 162abbae937e6eeae62dd9dfcd924af44dfd7270
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42610038"
---
# <a name="cloud-and-web-programming-in-visual-c"></a>Cloud et programmation Web dans Visual C++

En C++, vous disposez de plusieurs options de connexion web et cloud.

## <a name="cloud-programming-options"></a>Options de programmation de cloud

- [Microsoft Azure Mobile Services](http://www.windowsazure.com/develop/mobile/)

   Fournit des API natives que vous pouvez utiliser dans les applications de plateforme universelle Windows (UWP) ou des applications de bureau Windows pour se connecter à Windows Azure Mobile Services. Bien que la plupart des exemples présentés sur le site web soient en C#, vous pouvez aussi utiliser C++. Pour plus d’informations, consultez [Démarrage rapide : ajout d’un service mobile en C++](http://msdn.microsoft.com/library/windows/apps/dn263181.aspx).

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

- [Windows::Web::Http::HttpClient](https://msdn.microsoft.com/en-us/library/windows/apps/windows.web.http.httpclient.aspx)

   Classe de client HTTP Windows Runtime modélisée sur la classe .NET Framework du même nom dans l'espace de noms System.Web. `HttpClient` prend entièrement en charge le chargement et le téléchargement asynchrones via HTTP, ainsi que les filtres de pipeline qui permettent l'insertion de gestionnaires HTTP personnalisés dans le pipeline. Le Kit de développement logiciel (SDK) Windows inclut des exemples de filtres pour les connexions réseau limitées, l'authentification OAuth et bien plus encore. Pour les applications qui ciblent uniquement les plateforme Windows universelle, nous vous recommandons d’utiliser la `Windows::Web:HttpClient` classe. 

- [Interface IXMLHTTPRequest2](/previous-versions/windows/desktop/api/msxml6/nn-msxml6-ixmlhttprequest2)

   Fournit une interface COM native que vous pouvez utiliser dans les applications Windows Runtime ou des applications de bureau Windows pour se connecter à Internet via HTTP et émettre GET, PUT et d’autres commandes HTTP. Pour plus d’informations, consultez [procédure pas à pas : connexion à l’aide de tâches et les requêtes HTTP XML](../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md).

- [Windows Internet (WinInet)](http://msdn.microsoft.com/library/windows/desktop/aa385331\(v=vs.85\).aspx)

   API Windows que vous pouvez utiliser dans les applications de bureau Windows pour vous connecter à Internet.

## <a name="see-also"></a>Voir aussi

[Visual C++](../visual-cpp-in-visual-studio.md) <br/>
[Réseaux et services web](/windows/uwp/networking/)
