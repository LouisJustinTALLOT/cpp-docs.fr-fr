---
title: L’inscription | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- servers [MFC], initializing
- initializing servers [MFC]
- OLE, registration
- installing servers [MFC]
- registry [MFC], OLE item database
- registration databases [MFC]
- servers [MFC], installing
- OLE server applications [MFC], registering servers
ms.assetid: 991d5684-72c1-4f9e-a09a-9184ed12bbb9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e115edc4a7a276e04e886a0d7d324308dbe1c8ed
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46399585"
---
# <a name="registration"></a>Inscription

Lorsqu'un utilisateur souhaite insérer un élément OLE dans une application OLE, OLE présente une liste des types d'objets dans le but d'en choisir un. OLE obtient la liste de la base de données d'inscription du système, qui contient les informations fournies par les applications serveur. Lorsqu'un serveur s'inscrit lui-même, les entrées qu'il place dans la base de données d'inscription du système (le Registre) décrivent chaque type d'objet qu'il fournit, les extensions de fichier, le chemin d'accès à lui-même, parmi d'autres informations.

Le framework et les bibliothèques de liens dynamiques (DLL) du système OLE utilisent le Registre pour déterminer quels types d'éléments OLE sont disponibles dans le système. Les DLL système OLE utilisent également le Registre pour déterminer comment lancer une application serveur lorsqu'un objet lié ou incorporé est activé.

Cet article décrit ce que chaque application serveur doit effectuer lorsqu'elle est installée et chaque fois qu'elle est exécutée.

Pour obtenir des informations détaillées sur la base de données système d’inscription et le format des fichiers .reg utilisés pour mettre à jour, consultez le *référence du programmeur OLE*.

##  <a name="_core_server_installation"></a> Installation du serveur

Lors de l'installation initiale de votre application serveur, tous les types d'éléments OLE pris en charge doivent être inscrits. Il est également possible que le serveur actualise la base de données d'inscription du système à chaque fois qu'elle est exécutée comme une application autonome. Cela maintient la base de données d'inscription à jour si le fichier exécutable du serveur est déplacé.

> [!NOTE]
>  Les applications MFC générées par l'application Assistant s'inscrivent automatiquement elles-mêmes lorsqu'elles sont exécutées en tant qu'applications autonomes.

Si vous voulez enregistrer votre application pendant l'installation, utilisez le programme RegEdit.exe. Si vous incluez un programme d’installation avec votre application, ont le programme d’installation exécute « RegEdit /S *appname*.reg ». (L'indicateur /S indique l'opération silencieuse, c'est-à-dire qu'il n'affiche pas la boîte de dialogue qui signale la réussite de l'exécution de la commande.) Sinon, fournissez des instructions à l'utilisateur pour qu'il exécute le programme RegEdit manuellement.

> [!NOTE]
>  Le fichier .reg créé par l'assistant Application n'inclut pas de chemin d'accès complet du fichier exécutable. Le programme d’installation doit modifier le fichier .reg pour inclure le chemin d’accès complet au fichier exécutable ou modifier la variable d’environnement PATH pour inclure le répertoire d’installation.

RegEdit fusionne le contenu du fichier texte .reg dans la base de données d'inscription. Pour vérifier la base de données ou la réparer, utilisez l'Éditeur du Registre. Faites attention à ne pas supprimer des entrées OLE essentielles.

##  <a name="_core_server_initialization"></a> Initialisation du serveur

Lorsque vous créez une application serveur avec l’assistant Application, l’assistant termine toutes les tâches d’initialisation automatiquement. Cette section explique ce que vous devez faire si vous écrivez une application serveur manuellement.

Lorsqu'une application serveur est lancée par une application conteneur, les DLL système OLE ajoutent l'option "/Embedding" à la ligne de commande du serveur. Le comportement d'une application serveur diffère selon qu'elle a été exécutée par un conteneur, donc la première chose qu'une application doit effectuer lorsqu'elle commence à être exécutée est de contrôler l'option "/Embedding" ou "-Embedding" sur la ligne de commande. Si ce changement existe, chargez un autre ensemble de ressources qui montre le serveur comme étant actif sur place ou entièrement ouvert. Pour plus d’informations, consultez [Menus et ressources : ajouts de serveurs](../mfc/menus-and-resources-server-additions.md).

Votre application serveur doit également appeler la fonction `CWinApp::RunEmbedded` pour analyser la ligne de commande. Si elle retourne une valeur différente de zéro, l'application ne doit pas afficher sa fenêtre si elle a été exécutée à partir d'une application conteneur, et non comme application autonome. Cette fonction met à jour l'entrée de serveur dans la base de données d'inscription du système et appelle la fonction membre `RegisterAll` pour vous, qui effectue l'inscription d'instance.

Lorsque votre application serveur démarre, vous devez vous assurer qu'elle peut effectuer l'inscription d'instance. L'inscription d'instance informe les DLL du système OLE que le serveur est activé et prêt à recevoir des demandes issues des conteneurs. Elle n'ajoute pas d'entrée à la base de données d'inscription. Exécutez l'inscription de l'instance du serveur en appelant la fonction membre `ConnectTemplate` définie par `COleTemplateServer`. Cela connecte l'objet `CDocTemplate` à l'objet `COleTemplateServer`.

Le `ConnectTemplate` fonction accepte trois paramètres : le serveur *CLSID*, un pointeur vers le `CDocTemplate` objet et un indicateur qui spécifie si le serveur prend en charge plusieurs instances. Un mini-serveur doit prendre en charge plusieurs instances, c'est-à-dire qu'il est possible que plusieurs instances de serveurs s'exécutent simultanément, une pour chaque conteneur. Par conséquent, exécutez **TRUE** pour cet indicateur en lançant un mini-serveur.

Si vous entrez un mini-serveur par définition, il sera toujours exécuté par un conteneur. Vous devez toujours analyser la ligne de commande pour vérifier l'option "/Embedding". L'absence de cette option sur la ligne de commande indique que l'utilisateur a essayé de démarrer le mini-serveur en tant qu'application autonome. Si cela se produit, enregistrez le serveur avec la base de données d'inscription système, puis affichez un message informant l'utilisateur pour lancer le mini-serveur depuis une application conteneur.

## <a name="see-also"></a>Voir aussi

[OLE](../mfc/ole-in-mfc.md)<br/>
[Serveurs](../mfc/servers.md)<br/>
[CWinApp::RunAutomated](../mfc/reference/cwinapp-class.md#runautomated)<br/>
[CWinApp::RunEmbedded](../mfc/reference/cwinapp-class.md#runembedded)<br/>
[COleTemplateServer, classe](../mfc/reference/coletemplateserver-class.md)
