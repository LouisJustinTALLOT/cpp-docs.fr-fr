---
title: Wsadata, Structure | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- WSADATA
dev_langs:
- C++
helpviewer_keywords:
- WSADATA structure [MFC]
ms.assetid: 80cc60e5-f9ae-4290-8ed5-07003136627d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dadc502900285d879f2fd77af69b1fcf08a4ba1e
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2018
ms.locfileid: "37880929"
---
# <a name="wsadata-structure"></a>WSADATA, structure
La structure `WSADATA` permet de stocker les informations d'initialisation Windows Sockets retournées par un appel à la fonction globale `AfxSocketInit`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
struct WSAData {  
    WORD wVersion;  
    WORD wHighVersion;  
    char szDescription[WSADESCRIPTION_LEN+1];  
    char szSystemStatus[WSASYSSTATUS_LEN+1];  
    unsigned short iMaxSockets;  
    unsigned short iMaxUdpDg;  
    char FAR* lpVendorInfo;  
};  
```  
  
#### <a name="parameters"></a>Paramètres  
 *wVersion*  
 Version de la spécification Windows Sockets que la DLL Windows Sockets s'attend à voir utiliser par l'appelant.  
  
 *wHighVersion*  
 Version la plus récente de la spécification Windows Sockets que cette DLL peut prendre en charge (également encodée comme ci-dessus). En règle générale, cela est identique à *wVersion*.  
  
 *szDescription*  
 Chaîne ASCII terminée par le caractère NULL dans laquelle la DLL Windows Sockets copie une description de l'implémentation de Windows Sockets, y compris l'ID de fournisseur. Le texte (jusqu'à 256 caractères de longueur) peut contenir tous les caractères, mais les fournisseurs savent qu'ils ne doivent pas utiliser les caractères de mise en forme et de contrôle (affichage probablement tronqué dans un message d'état).  
  
 *szSystemStatus*  
 Chaîne ASCII terminée par le caractère NULL dans laquelle la DLL Windows Sockets copie des informations pertinentes sur l'état ou la configuration. La DLL de Sockets Windows doit utiliser ce champ uniquement si les informations peuvent être utiles à l’utilisateur ou prennent en charge un personnel ; elle ne doit pas être considérée comme une extension de la *szDescription* champ.  
  
 *iMaxSockets*  
 Nombre maximal de sockets qu'un seul processus peut potentiellement ouvrir. Une implémentation Windows Sockets peut fournir un pool global de sockets pour l'allocation à tout processus ; sinon, elle peut allouer des ressources par processus aux sockets. Le nombre peut ainsi réfléchir la façon dont la DLL Windows Sockets ou le logiciel réseau a été configuré. Les programmes d'écriture d'applications peuvent utiliser ce nombre comme une indication brute au cas où l'implémentation de Windows Sockets serait utilisable par l'application. Par exemple, un serveur X Windows peut vérifier *iMaxSockets* lors du premier démarrage : s’il est inférieur à 8, l’application affichera un message d’erreur demandant à l’utilisateur pour reconfigurer le logiciel réseau. (Il s’agit d’une situation dans laquelle le *szSystemStatus* texte peut être utilisé.) Évidemment, il n’existe aucune garantie qu’une application particulière peut allouer *iMaxSockets* sockets, dans la mesure où il peut y avoir des autres applications Windows Sockets en cours d’utilisation.  
  
 *iMaxUdpDg*  
 Taille en octets du plus grand datagramme de protocole utilisateur (UDP) qui peut être envoyé ou reçu par une application Windows Sockets. Si l’implémentation n’impose aucune limite, *iMaxUdpDg* est égal à zéro. Dans la plupart des implémentations des sockets à Berkeley, il existe une limite implicite de 8192 octets sur les datagrammes UDP (qui sont réduits en fragments si nécessaire). Une implémentation Windows Sockets peut imposer une limite basée, par exemple, sur l'allocation des tampons de réassemblage de fragment. La valeur minimale de *iMaxUdpDg* pour un Sockets Windows conforme implémentation est 512. Notez que, quel que soit la valeur de *iMaxUdpDg*, il est déconseillé de tenter d’envoyer un datagramme diffusé qui est supérieur à l’unité de Transmission maximale (MTU) pour le réseau. (L'API Windows Sockets ne fournit pas de mécanisme permettant de déterminer la MTU, mais elle ne doit pas être inférieure à 512 octets.)  
  
 *lpVendorInfo*  
 Un pointeur lointain vers une structure de données spécifique au fournisseur. La définition de cette structure (si disponible) dépasse le cadre de la spécification de Windows Sockets.  
  
> [!NOTE]
>  Dans MFC, la structure `WSADATA` est retournée par la fonction `AfxSocketInit`, que vous appelez dans votre fonction `InitInstance`. Vous pouvez récupérer la structure et l'enregistrer dans votre programme si vous devez utiliser les informations ultérieurement.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** winsock2.h  
  
## <a name="see-also"></a>Voir aussi  
 [Structures, Styles, rappels et tables des messages](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)

