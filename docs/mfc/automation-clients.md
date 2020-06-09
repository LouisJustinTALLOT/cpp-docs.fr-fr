---
title: Clients Automation
ms.date: 11/04/2016
helpviewer_keywords:
- clients, Automation
- Automation clients
- type libraries, Automation clients
- clients
ms.assetid: 84e34a79-06f6-4752-a33b-ae0ede1d8ecf
ms.openlocfilehash: 9c34f6fccd06635dfb686e6eb1f2cf895bb86989
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626081"
---
# <a name="automation-clients"></a>Clients Automation

L'Automation rend possible pour votre application la manipulation d'objets implémentés dans une autre application, ou l'exposition d'objets pour qu'ils puissent être manipulés. Un client Automation est une application qui peut manipuler des objets exposés appartenant à une autre application. L’application qui expose les objets est appelée serveur Automation. Le client manipule les objets de l’application serveur en accédant aux propriétés et fonctions de ces objets.

### <a name="types-of-automation-clients"></a>Types de clients Automation

Il existe deux types de clients Automation :

- Les clients qui acquièrent dynamiquement (au moment de l’exécution) des informations sur les propriétés et les opérations du serveur.

- Clients qui possèdent des informations statiques (fournies au moment de la compilation) qui spécifient les propriétés et les opérations du serveur.

Les clients du premier type acquièrent des informations sur les méthodes et les propriétés du serveur en interrogeant le mécanisme du système OLE `IDispatch` . Bien qu’il soit approprié d’utiliser pour les clients dynamiques, `IDispatch` est difficile à utiliser pour les clients statiques, où les objets pilotés doivent être connus au moment de la compilation. Pour les clients liés statiques, les classes Microsoft Foundation fournissent la classe [COleDispatchDriver](reference/coledispatchdriver-class.md) .

Les clients liés statiques utilisent une classe proxy qui est liée de manière statique à l’application cliente. Cette classe fournit une encapsulation C++ de type sécurisé des propriétés et opérations de l’application serveur.

La classe `COleDispatchDriver` fournit la prise en charge principale du côté client de l’Automation. À l’aide de la boîte de dialogue **Ajouter un nouvel élément** , vous créez une classe dérivée de `COleDispatchDriver` .

Vous spécifiez ensuite le fichier de bibliothèque de types décrivant les propriétés et les fonctions de l’objet de l’application serveur. La boîte de dialogue Ajouter un élément lit ce fichier et crée la `COleDispatchDriver` classe dérivée de, avec les fonctions membres que votre application peut appeler pour accéder aux objets de l’application serveur en C++ de manière sécurisée. Les fonctionnalités supplémentaires héritées de `COleDispatchDriver` simplifient le processus d’appel du serveur Automation approprié.

### <a name="handling-events-in-automation-clients"></a>Gestion des événements dans les clients Automation

Si vous souhaitez gérer des événements dans votre client Automation, vous devez ajouter une interface de récepteur. MFC fournit la prise en charge de l’Assistant pour ajouter des interfaces sink pour les contrôles ActiveX, mais ne prend pas en charge les autres serveurs COM.

## <a name="see-also"></a>Voir aussi

[Clients Automation : utilisation des bibliothèques de types](automation-clients-using-type-libraries.md)<br/>
[Automation](automation.md)<br/>
[Assistant Application MFC](reference/mfc-application-wizard.md)
