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
ms.openlocfilehash: ce9042a980190bf1fe3da06fb4a9843f73294dee
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46398844"
---
# <a name="idl-attributes-add-method-wizard"></a>Attributs IDL, Assistant Ajout de méthode

Utilisez cette page de l’Assistant Ajout de méthode pour spécifier tous les paramètres IDL (Interface Definition Language) de la méthode.

- **ID**

   Définit l’ID numérique qui identifie la méthode. Consultez [id](/windows/desktop/Midl/id) dans les *Informations de référence MIDL*.

   Cette zone n’est pas disponible pour les interfaces personnalisées ni pour les dispinterfaces MFC.

- **call_as**

   Spécifie le nom d’une méthode distante à laquelle cette méthode locale peut être mappée. Consultez [call_as](/windows/desktop/Midl/call-as) dans les *Informations de référence MIDL*.

   Non disponible pour les dispinterfaces MFC.

- **helpcontext**

   Spécifie un ID de contexte qui permet à l'utilisateur de voir des informations sur cette méthode dans le fichier d’aide. Consultez [helpcontext](/windows/desktop/Midl/helpcontext) dans les *Informations de référence MIDL*.

   Non disponible pour les dispinterfaces MFC.

- **helpstring**

   Spécifie une chaîne de caractères qui est utilisée pour décrire l’élément auquel elle s’applique. Par défaut, il est défini sur « method *nom de la méthode* ». Consultez [helpstring](/windows/desktop/Midl/helpstring) dans les *Informations de référence MIDL*.

   Non disponible pour les dispinterfaces MFC.

- **Attributs supplémentaires**

   Non disponible pour les dispinterfaces MFC.

   |Attribut|Description|
   |---------------|-----------------|
   |**hidden**|Indique que la méthode existe, mais qu’elle ne doit pas être affichée dans un navigateur orienté utilisateur. Consultez [hidden](/windows/desktop/Midl/hidden) dans les *Informations de référence MIDL*.|
   |**source**|Indique qu’un membre de la méthode est une source d’événements. Consultez [source](/windows/desktop/Midl/source) dans les *Informations de référence MIDL*.|
   |`local`|Spécifie au compilateur MIDL que la méthode n’est pas distante. Consultez [local](/windows/desktop/Midl/local) dans les *Informations de référence MIDL*.|
   |**restricted**|Spécifie que la méthode ne peut pas être appelée arbitrairement. Consultez [restricted](/windows/desktop/Midl/restricted) dans les *Informations de référence MIDL*.|
   |**vararg**|Spécifie que la méthode accepte un nombre variable d’arguments. Le dernier argument doit être un tableau sécurisé de type **VARIANT** qui contient tous les arguments restants. Consultez [vararg](/windows/desktop/Midl/vararg) dans les *Informations de référence MIDL*.|

## <a name="see-also"></a>Voir aussi

[Ajout d’une méthode](../ide/adding-a-method-visual-cpp.md)<br>
[Assistant Ajout de méthode](../ide/add-method-wizard.md)