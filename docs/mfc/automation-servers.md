---
description: 'En savoir plus sur : serveurs Automation'
title: Serveurs Automation
ms.date: 11/04/2016
helpviewer_keywords:
- Automation servers
- COM components, Automation servers
- dispatch maps [MFC], Automation servers
- servers, Automation
ms.assetid: 523fd155-51ce-4f91-b986-b74bdbdd7d92
ms.openlocfilehash: e97bcf524b96e459cd1a3caddec7cdaf0c030962
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97339824"
---
# <a name="automation-servers"></a>Serveurs Automation

L'Automation rend possible pour votre application la manipulation d'objets implémentés dans une autre application, ou l'exposition d'objets pour qu'ils puissent être manipulés. Un serveur Automation est une application qui expose des objets programmables (appelés objets Automation) à d’autres applications (appelées [clients Automation](automation-clients.md)). Les serveurs Automation sont parfois appelés composants Automation.

L'exposition des objets Automation permet aux clients d'automatiser certaines procédures en accédant directement aux objets et aux fonctionnalités que le serveur rend disponibles. L'exposition des objets de cette manière est bénéfique lorsque les applications fournissent des fonctionnalités qui sont utiles à d'autres applications. Par exemple, un traitement de texte peut exposer sa fonctionnalité de vérification d'orthographe pour qu'un autre programme puisse l'utiliser. L'exposition d'objets permet alors aux fournisseurs d'améliorer les fonctionnalités de leurs applications en utilisant la fonctionnalité prête à l'emploi d'autres applications.

Ces objets Automation possèdent des propriétés et des méthodes qui leur servent d'interface externe. Les propriétés sont appelées les attributs des objets Automation. Les propriétés sont comme les membres de données d'une classe C++. Les méthodes sont des fonctions qui utilisent des objets Automation. Les méthodes sont comme les fonctions membres publiques d'une classe en C++.

> [!NOTE]
> Bien que les propriétés sont comme les membres de données C++, elles ne sont pas directement accessibles. Pour fournir un accès transparent, installez une variable interne dans l'objet Automation avec une paire de fonctions get/set pour y accéder.

En exposant des fonctionnalités d'application via une interface commune et bien définie, Automation permet de générer des applications dans un seul langage de programmation général, tel que Microsoft Visual Basic, et non pas dans des langages macros spécifiques à chaque application.

## <a name="support-for-automation-servers"></a><a name="_core_support_for_automation_servers"></a> Prise en charge des serveurs Automation

Visual C++ et le framework MFC fournissent la prise en charge complète des serveurs Automation. Ils gèrent une grande partie de la charge mémoire générée par un serveur Automation, donc vous pouvez concentrer vos efforts sur la fonctionnalité de votre application.

Le mécanisme principal du framework pour la prise en charge de l’Automation est la table de dispatch, un ensemble de macros qui se développe en déclarations et en appels nécessaires pour exposer les méthodes et les propriétés pour OLE. Une table de dispatch classique ressemble à ceci :

[!code-cpp[NVC_MFCAutomation#1](codesnippet/cpp/automation-servers_1.cpp)]

L' [Assistant classe](reference/mfc-class-wizard.md) et affichage de classes aider à gérer les tables de dispatch. Quand vous ajoutez une nouvelle méthode ou propriété à une classe, Visual Studio ajoute une `DISP_FUNCTION` macro ou correspondante `DISP_PROPERTY` avec des paramètres indiquant le nom de la classe, les noms externes et internes de la méthode ou de la propriété, ainsi que les types de données.

La boîte de dialogue **Ajouter une classe** simplifie également la déclaration des classes Automation et la gestion de leurs propriétés et opérations. Lorsque vous utilisez la boîte de dialogue Ajouter une classe pour ajouter une classe à votre projet, vous spécifiez sa classe de base. Si la classe de base permet l'Automation, la boîte de dialogue Ajouter une classe affiche les contrôles que vous utilisez pour spécifier si la nouvelle classe doit prendre en charge l'Automation, si elle "peut être créée avec OLE" (autrement dit, si les objets de la classe peuvent être créés sur une requête d'un client COM), ainsi que le nom externe pour que le client COM l'utilise.

La boîte de dialogue **Ajouter une classe** crée ensuite une déclaration de classe, y compris les macros appropriées pour les fonctionnalités OLE que vous avez spécifiées. Elle ajoute également le squelette du code pour l'implémentation des fonctions membres de votre classe.

L'Assistant Application MFC simplifie les étapes d'obtention de l'application serveur Automation à partir de rien. Si vous activez la case à cocher **Automation** à partir de la page **fonctionnalités avancées** , l’Assistant Application MFC ajoute à la fonction de votre application `InitInstance` les appels requis pour inscrire vos objets Automation et exécuter votre application en tant que serveur Automation.

### <a name="what-do-you-want-to-do"></a>Tu veux faire quoi

- [En savoir plus sur les clients Automation](automation-clients.md)

- [En savoir plus sur la classe CCmdTarget](reference/ccmdtarget-class.md)

- [En savoir plus sur la classe COleDispatchDriver](reference/coledispatchdriver-class.md)

## <a name="see-also"></a>Voir aussi

[Automation](automation.md)<br/>
[Assistant Application MFC](reference/mfc-application-wizard.md)
