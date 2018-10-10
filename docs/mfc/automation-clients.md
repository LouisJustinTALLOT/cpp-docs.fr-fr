---
title: Les Clients Automation | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- clients, Automation
- Automation clients
- type libraries, Automation clients
- clients
ms.assetid: 84e34a79-06f6-4752-a33b-ae0ede1d8ecf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cdc9b47bbd7b639850a13a77b81ef4802a301ba7
ms.sourcegitcommit: d3c41b16bf05af2149090e996d8e71cd6cd55c7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/09/2018
ms.locfileid: "48890060"
---
# <a name="automation-clients"></a>Clients Automation

L'Automation rend possible pour votre application la manipulation d'objets implémentés dans une autre application, ou l'exposition d'objets pour qu'ils puissent être manipulés. Un client Automation est une application qui peut manipuler des objets exposés appartenant à une autre application. L’application qui expose les objets est appelée serveur Automation. Le client manipule les objets de l’application serveur en accédant aux propriétés et fonctions de ces objets.

### <a name="types-of-automation-clients"></a>Types de Clients Automation

Il existe deux types de clients Automation :

- Clients dynamiquement (au moment de l’exécution) acquièrent des informations sur les propriétés et opérations du serveur.

- Clients qui possèdent des informations statiques (fournies au moment de la compilation) qui spécifie les propriétés et opérations du serveur.

Les clients de première espèce acquièrent des informations sur les méthodes et les propriétés du serveur en interrogeant le système OLE `IDispatch` mécanisme. Même si elle est suffisante pour utiliser des clients dynamiques, `IDispatch` est difficile à utiliser pour les clients statiques, où les objets qui est contrôlée doit être connu au moment de la compilation. Pour statique liées aux clients, Microsoft Foundation classes fournissent la [COleDispatchDriver](../mfc/reference/coledispatchdriver-class.md) classe.

Clients avec liaison statique utilisent une classe proxy qui est liée de manière statique avec l’application cliente. Cette classe fournit une encapsulation C++ de type sécurisé de propriétés et opérations de l’application serveur.

La classe `COleDispatchDriver` fournit la prise en charge du principal pour le côté client d’Automation. À l’aide de la **ajouter un nouvel élément** boîte de dialogue, vous créez une classe dérivée de `COleDispatchDriver`.

Vous spécifiez ensuite le fichier de bibliothèque de types décrivant les propriétés et les fonctions de l’objet de l’application serveur. La boîte de dialogue Ajouter un élément lit ce fichier et crée le `COleDispatchDriver`-classe dérivée, avec des fonctions de membre qui votre application peut appeler pour accéder aux objets de l’application serveur en C++ de manière sécurisée. Héritent de fonctionnalités supplémentaires `COleDispatchDriver` simplifie le processus d’appel du serveur Automation approprié.

### <a name="handling-events-in-automation-clients"></a>Gestion des événements dans les Clients Automation

Si vous souhaitez gérer des événements dans votre client automation, vous devez ajouter une interface de récepteur. MFC fournit la prise en charge de l’Assistant pour ajouter des interfaces de récepteur pour les contrôles ActiveX, mais pas en charge pour les autres serveurs COM.

## <a name="see-also"></a>Voir aussi

[Clients Automation : utilisation des bibliothèques de types](../mfc/automation-clients-using-type-libraries.md)<br/>
[Automation](../mfc/automation.md)<br/>
[Assistant Application MFC](../mfc/reference/mfc-application-wizard.md)

