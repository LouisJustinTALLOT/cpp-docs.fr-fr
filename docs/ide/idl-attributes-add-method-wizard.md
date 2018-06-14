---
title: Attributs IDL, Assistant Ajout de méthode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- vc.codewiz.method.idlattrib
dev_langs:
- C++
helpviewer_keywords:
- Add Method Wizard [C++]
- IDL attributes, Add Method Wizard
ms.assetid: f80c3bc1-b515-4d6c-83ee-98c2c21ba902
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4a7a1e8fe89f64ad5909e7c1415545e3b3d80196
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33337767"
---
# <a name="idl-attributes-add-method-wizard"></a>Attributs IDL, Assistant Ajout de méthode
Utilisez cette page de l’Assistant Ajout de méthode pour spécifier tous les paramètres IDL (Interface Definition Language) de la méthode.  
  
 **ID**  
 Définit l’ID numérique qui identifie la méthode. Consultez [id](http://msdn.microsoft.com/library/windows/desktop/aa367040) dans les *Informations de référence MIDL*.  
  
 Cette zone n’est pas disponible pour les interfaces personnalisées ni pour les dispinterfaces MFC.  
  
 **call_as**  
 Spécifie le nom d’une méthode distante à laquelle cette méthode locale peut être mappée. Consultez [call_as](http://msdn.microsoft.com/library/windows/desktop/aa366748) dans les *Informations de référence MIDL*.  
  
 Non disponible pour les dispinterfaces MFC.  
  
 **helpcontext**  
 Spécifie un ID de contexte qui permet à l'utilisateur de voir des informations sur cette méthode dans le fichier d’aide. Consultez [helpcontext](http://msdn.microsoft.com/library/windows/desktop/aa366851) dans les *Informations de référence MIDL*.  
  
 Non disponible pour les dispinterfaces MFC.  
  
 **helpstring**  
 Spécifie une chaîne de caractères qui est utilisée pour décrire l’élément auquel elle s’applique. Par défaut, il est défini sur « method *nom de la méthode* ». Consultez [helpstring](http://msdn.microsoft.com/library/windows/desktop/aa366856) dans les *Informations de référence MIDL*.  
  
 Non disponible pour les dispinterfaces MFC.  
  
 **Attributs supplémentaires**  
 Non disponible pour les dispinterfaces MFC.  
  
|Attribut|Description|  
|---------------|-----------------|  
|**hidden**|Indique que la méthode existe, mais qu’elle ne doit pas être affichée dans un navigateur orienté utilisateur. Consultez [hidden](http://msdn.microsoft.com/library/windows/desktop/aa366861) dans les *Informations de référence MIDL*.|  
|**source**|Indique qu’un membre de la méthode est une source d’événements. Consultez [source](http://msdn.microsoft.com/library/windows/desktop/aa367166) dans les *Informations de référence MIDL*.|  
|`local`|Spécifie au compilateur MIDL que la méthode n’est pas distante. Consultez [local](http://msdn.microsoft.com/library/windows/desktop/aa367071) dans les *Informations de référence MIDL*.|  
|**restricted**|Spécifie que la méthode ne peut pas être appelée arbitrairement. Consultez [restricted](http://msdn.microsoft.com/library/windows/desktop/aa367157) dans les *Informations de référence MIDL*.|  
|**vararg**|Spécifie que la méthode accepte un nombre variable d’arguments. Le dernier argument doit être un tableau sécurisé de type **VARIANT** qui contient tous les arguments restants. Consultez [vararg](http://msdn.microsoft.com/library/windows/desktop/aa367304) dans les *Informations de référence MIDL*.|  
  
## <a name="see-also"></a>Voir aussi  
 [Ajout d’une méthode](../ide/adding-a-method-visual-cpp.md)   
 [Assistant Ajout de méthode](../ide/add-method-wizard.md)