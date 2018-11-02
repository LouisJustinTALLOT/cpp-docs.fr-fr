---
title: Serveurs Automation
ms.date: 11/04/2016
helpviewer_keywords:
- Automation servers
- COM components, Automation servers
- dispatch maps [MFC], Automation servers
- servers, Automation
ms.assetid: 523fd155-51ce-4f91-b986-b74bdbdd7d92
ms.openlocfilehash: 0c7f3a3bd37c5f7f5696de363aa646f5376f4e75
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50468794"
---
# <a name="automation-servers"></a>Serveurs Automation

L'Automation rend possible pour votre application la manipulation d'objets implémentés dans une autre application, ou l'exposition d'objets pour qu'ils puissent être manipulés. Un serveur Automation est une application qui expose des objets programmables (appelés objets Automation) à d’autres applications (appelé [clients Automation](../mfc/automation-clients.md)). Les serveurs Automation sont parfois appelés composants Automation.

L'exposition des objets Automation permet aux clients d'automatiser certaines procédures en accédant directement aux objets et aux fonctionnalités que le serveur rend disponibles. L'exposition des objets de cette manière est bénéfique lorsque les applications fournissent des fonctionnalités qui sont utiles à d'autres applications. Par exemple, un traitement de texte peut exposer sa fonctionnalité de vérification d'orthographe pour qu'un autre programme puisse l'utiliser. L'exposition d'objets permet alors aux fournisseurs d'améliorer les fonctionnalités de leurs applications en utilisant la fonctionnalité prête à l'emploi d'autres applications.

Ces objets Automation possèdent des propriétés et des méthodes qui leur servent d'interface externe. Les propriétés sont appelées les attributs des objets Automation. Les propriétés sont comme les membres de données d'une classe C++. Les méthodes sont des fonctions qui utilisent des objets Automation. Les méthodes sont comme les fonctions membres publiques d'une classe en C++.

> [!NOTE]
>  Bien que les propriétés sont comme les membres de données C++, elles ne sont pas directement accessibles. Pour fournir un accès transparent, installez une variable interne dans l'objet Automation avec une paire de fonctions get/set pour y accéder.

En exposant des fonctionnalités d'application via une interface commune et bien définie, Automation permet de générer des applications dans un seul langage de programmation général, tel que Microsoft Visual Basic, et non pas dans des langages macros spécifiques à chaque application.

##  <a name="_core_support_for_automation_servers"></a> Prise en charge pour les serveurs Automation

Visual C++ et le framework MFC fournissent la prise en charge complète des serveurs Automation. Ils gèrent une grande partie de la charge mémoire générée par un serveur Automation, donc vous pouvez concentrer vos efforts sur la fonctionnalité de votre application.

Le mécanisme principal du framework pour la prise en charge de l'Automation est la table de dispatch, un ensemble de macros qui s'étend dans les déclarations et les appels nécessaires pour exposer les méthodes et les propriétés pour OLE. Une table de dispatch classique ressemble à ceci :

[!code-cpp[NVC_MFCAutomation#1](../mfc/codesnippet/cpp/automation-servers_1.cpp)]

La fenêtre Propriétés et l'Affichage de classes aident à maintenir les tables de dispatch. Lorsque vous ajoutez une nouvelle méthode ou propriété à une classe, Visual C++ ajoute une macro correspondant à `DISP_FUNCTION` ou `DISP_PROPERTY` avec des paramètres indiquant le nom de la classe, les noms externes et internes de la méthode ou de la propriété, ainsi que les types de données.

Le **ajouter une classe** boîte de dialogue simplifie également la déclaration des classes Automation et la gestion de leurs propriétés et opérations. Lorsque vous utilisez la boîte de dialogue Ajouter une classe pour ajouter une classe à votre projet, vous spécifiez sa classe de base. Si la classe de base permet l'Automation, la boîte de dialogue Ajouter une classe affiche les contrôles que vous utilisez pour spécifier si la nouvelle classe doit prendre en charge l'Automation, si elle "peut être créée avec OLE" (autrement dit, si les objets de la classe peuvent être créés sur une requête d'un client COM), ainsi que le nom externe pour que le client COM l'utilise.

Le **ajouter une classe** boîte de dialogue crée ensuite une déclaration de classe, y compris les macros appropriées pour les fonctionnalités OLE vous avez spécifié. Elle ajoute également le squelette du code pour l'implémentation des fonctions membres de votre classe.

L'Assistant Application MFC simplifie les étapes d'obtention de l'application serveur Automation à partir de rien. Si vous sélectionnez le **Automation** case à cocher à partir de la **fonctionnalités avancées** page, l’Assistant Application MFC ajoute à votre application `InitInstance` les appels nécessaires pour inscrire votre Automation de fonction les objets et exécuter votre application en tant que serveur Automation.

### <a name="what-do-you-want-to-do"></a>Tu veux faire quoi

- [En savoir plus sur les clients Automation](../mfc/automation-clients.md)

- [En savoir plus sur la classe CCmdTarget](../mfc/reference/ccmdtarget-class.md)

- [En savoir plus sur la classe COleDispatchDriver](../mfc/reference/coledispatchdriver-class.md)

## <a name="see-also"></a>Voir aussi

[Automation](../mfc/automation.md)<br/>
[Assistant Application MFC](../mfc/reference/mfc-application-wizard.md)

