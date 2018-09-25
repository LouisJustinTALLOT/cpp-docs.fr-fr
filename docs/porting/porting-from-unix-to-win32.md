---
title: Portage d’UNIX vers Win32 | Microsoft Docs
ms.custom: ''
ms.date: 08/02/2018
ms.technology:
- cpp-language
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- APIs [C++], porting to Win32
- Windows API [C++], migrating from UNIX
- migration [C++]
- UNIX [C++], porting to Win32
- porting to Win32 [C++], from UNIX
- porting to Win32 [C++]
- Win32 applications [C++], migrating from UNIX
ms.assetid: 3837e4fe-3f96-4f24-b2a1-7be94718a881
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a5dddac6d5e8b5be1b99d9c8004fcaa36d6b0b30
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46394029"
---
# <a name="porting-from-unix-to-win32"></a>Portage d'UNIX vers Win32

Pour effectuer la migration d'applications d'UNIX vers Windows, vous avez le choix entre plusieurs options :  
  
- Utiliser des bibliothèques UNIX pour porter les applications d'UNIX vers Win32  
  
- Porter des applications d'UNIX vers Win32 en mode natif  
  
- Exécuter les applications UNIX sous Windows à l'aide du sous-système POSIX  
  
## <a name="unix-libraries"></a>Bibliothèques UNIX  
 
Une option généralement envisagée par les programmeurs UNIX consiste à utiliser des bibliothèques tierces de type UNIX pour compiler leur code UNIX comme un exécutable Win32. Plusieurs bibliothèques commercialisées (et au moins une dans le domaine public) offrent cette possibilité. Certaines applications le proposent en tant qu'option. Ces bibliothèques de portage présentent l'avantage de réduire le travail de portage initial. Leur principal inconvénient, pour un logiciel soumis à la concurrence, est que le portage Win32 en mode natif d'une application est généralement plus rapide et incontestablement plus riche en fonctionnalités. Il peut s'avérer difficile pour l'application de sortir de son shell UNIX si elle doit effectuer des appels Win32 pour mieux exploiter la puissance de Windows.  
  
La liste suivante indique les ressources Microsoft et tierces disponibles pour le portage et la prise en charge de la migration d'UNIX vers Visual C++ :  
  
### <a name="unix-migration-guides"></a>Guides de migration d'UNIX  
Le manuel [UNIX Custom Application Migration Guide](https://technet.microsoft.com/library/bb656290.aspx) fournit une aide technique sur la migration du code de l'environnement UNIX vers l'environnement Win32.  
  
Le manuel [Unix Migration Project Guide](https://technet.microsoft.com/library/bb656287.aspx) vient compléter le manuel « UNIX Custom Application Migration Guide » en proposant une aide détaillée sur la migration de projets majeurs d'UNIX vers Win32. Ce guide fournit des conseils relatifs aux problèmes susceptibles de se produire aux différentes étapes de la migration d'un projet.
  
### <a name="microsoft-windows-services-for-unix-sfu"></a>Microsoft Windows Services for UNIX (SFU)  
Microsoft Windows Services for UNIX (SFU) fournit une gamme complète de services multiplateforme pour intégrer Windows dans les environnements UNIX existants. Ces services permettent le partage de fichiers, l’administration et l’accès à distance, la synchronisation de mot de passe et la gestion d’annuaires communs. Ils fournissent aussi un ensemble d’utilitaires communs et un shell.  
  
[Windows Services for UNIX](http://www.microsoft.com/downloads/details.aspx?FamilyID=896c9688-601b-44f1-81a4-02878ff11778&displaylang=en)  
  
### <a name="interopsystemscom"></a>InteropSystems.com  
[http://www.interopsystems.com/](http://www.interopsystems.com/)  
  
Il s'agit du site d'une société tierce qui fournit des solutions logicielles de prise en charge du portage d'UNIX vers Win32.  
  
### <a name="c-boost-web-site"></a>Site web C++ Boost  
[http://boost.sourceforge.net/regression-logs/](http://boost.sourceforge.net/regression-logs/)  
  
[http://boost.sourceforge.net/boost-build2/](http://boost.sourceforge.net/boost-build2/)  
  
## <a name="porting-unix-applications-directly-to-win32"></a>Portage d'applications UNIX directement vers Win32  
 
Une autre option consiste à porter les applications UNIX directement vers Win32. Grâce aux bibliothèques C/C++ ANSI et aux bibliothèques du compilateur C disponibles dans le commerce, la plupart des appels système classiques sur lesquels s'appuient les applications UNIX sont possibles dans les applications Win32.  
  
Le modèle de sortie des applications **stdio** ne nécessite aucune modification, car les API de console Win32 simulent ce modèle **stdio**, et il existe des versions de *curses* qui utilisent les API de console Win32. Pour plus d’informations, consultez [SetConsoleCursorPosition](https://msdn.microsoft.com/library/windows/desktop/ms686025).  
  
Les applications qui utilisent des sockets Berkeley nécessitent très peu de modifications pour fonctionner comme des applications Win32. L'interface Windows Sockets a été conçue pour garantir la portabilité avec les sockets BSD, moyennant quelques modifications mineures, comme indiqué dans les sections d'introduction de la spécification WinSock.  
  
Windows prend en charge le RPC conforme à DCE, ce qui rend les applications basées sur RPC facilement utilisables. Consultez [Fonctions RPC](/windows/desktop/Rpc/rpc-functions).  
  
L'une des principales différences réside dans le modèle de processus. UNIX utilise le processus `fork`, ce qui n’est pas le cas de Win32. En fonction de l’utilisation de `fork` et de la base de code, vous avez le choix entre ces deux API Win32 : `CreateProcess` et `CreateThread`. Une application UNIX qui duplique plusieurs copies d'elle-même peut être modifiée dans Win32 de façon à avoir plusieurs processus ou un seul processus avec plusieurs threads. Si plusieurs processus sont utilisés, différentes méthodes d’IPC sont disponibles pour établir la communication entre les processus (et éventuellement pour mettre à jour le code et les données du nouveau processus par rapport au parent, si la fonctionnalité assurée par `fork` est nécessaire). Pour plus d’informations sur IPC, consultez [Communications entre processus](/windows/desktop/ipc/interprocess-communications).  
  
Les modèles graphiques UNIX et Windows sont très différents. UNIX utilise l'interface GUI du système X Window, alors que Windows utilise l'interface GDI. Les deux sont similaires d'un point de vue conceptuel, mais il n'existe pas de mappage simple entre l'API X et l'API GDI. Toutefois, une prise en charge OpenGL est disponible pour faire migrer des applications OpenG UNIX. Il existe en outre des clients X et des serveurs X pour Windows. Pour plus d’informations sur GDI, consultez [Contextes de périphérique](https://msdn.microsoft.com/library/windows/desktop/dd183553).  
  
Les applications UNIX de base, y compris de nombreuses applications CGI, peuvent normalement être portées facilement vers Visual C++ sous Windows. Des fonctions comme `open`, `fopen`, `read` et `write`, parmi d’autres, sont disponibles dans la bibliothèque Runtime Visual C++. En outre, un mappage un-à-un est possible entre les API C UNIX et les API Win32 : `open` et `CreateFile`, `read` et `ReadFile`, `write` et `WriteFile`, `ioctl` et `DeviceIOControl`, `close` et `CloseFile`, etc.  
  
## <a name="windows-posix-subsystem"></a>Sous-système POSIX sous Windows  
 
Une autre option étudiée par les programmeurs UNIX est celle du sous-système POSIX sous Windows. Toutefois, seule la version 1003.1 de POSIX, qui est l'unique version ayant été normalisée au lancement de Windows NT, est prise en charge. Depuis, la demande pour une extension de ce sous-système a été faible, la plupart des applications ayant été converties en Win32. Le système 1003.1 présente un intérêt limité pour les applications complètes, car de nombreuses fonctionnalités lui font défaut (notamment celles de la version 1003.2, la prise en charge réseau, etc.). Les applications complètes exécutées sur le sous-système POSIX sous Windows n'ont pas accès aux fonctionnalités de Windows disponibles dans les applications Win32, telles que les fichiers mappés en mémoire, la mise en réseau et les graphiques. Les applications telles que VI, LS et GREP sont les principales cibles du sous-système POSIX sous Windows.  
  
## <a name="see-also"></a>Voir aussi  
 
[Guide du portage et de la mise à niveau de Visual C++](visual-cpp-change-history-2003-2015.md)<br/>
[UNIX](../c-runtime-library/unix.md)<br/>
[Règles d’inférence](../build/inference-rules.md)