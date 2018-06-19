---
title: Insertion d’un contrôle sur une Page Web (didacticiel ATL, partie 7) | Documents Microsoft
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 50dc4c95-c95b-4006-b88a-9826f7bdb222
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0cd4076ac34af6ee4b19687f401376265bf0e872
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32362582"
---
# <a name="putting-the-control-on-a-web-page-atl-tutorial-part-7"></a>Insertion d’un contrôle sur une page web (Didacticiel ATL, Partie 7)
Votre contrôle est maintenant terminé. Pour voir votre contrôle fonctionne dans une situation réelle, vous devez le placer sur une page Web. Un fichier HTML qui contient le contrôle a été créé lorsque vous avez défini votre contrôle. Ouvrez le fichier PolyCtl.htm **l’Explorateur de solutions**, et vous pouvez voir votre contrôle sur une page Web.  
  
 Dans cette étape, vous allez utiliser le script la page Web pour répondre aux événements. Vous allez également modifier le contrôle pour permettre à Internet Explorer de savoir que le contrôle est sécurisé pour le script.  
  
## <a name="scripting-the-web-page"></a>Script de la Page Web  
 Le contrôle ne pas faire quelque chose encore, par conséquent, de modifier la page Web pour répondre aux événements que vous envoyez.  
  
#### <a name="to-script-the-web-page"></a>Créer un script de la page Web  
  
1.  Ouvrez PolyCtl.htm et sélectionnez le mode HTML. Ajoutez les lignes suivantes au code HTML. Elles doivent être ajoutées après `</OBJECT>` mais avant que `</BODY>`.  
  
 ```  
 
 <SCRIPT LANGUAGE="VBScript">  
 <!--  
    Sub PolyCtl_ClickIn(x, y)  
    PolyCtl.Sides = PolyCtl.Sides + 1  
    End Sub  
    Sub PolyCtl_ClickOut(x, y)  
    PolyCtl.Sides = PolyCtl.Sides - 1  
    End Sub  
 -->  
 </SCRIPT>  
 ```  
  
2.  Enregistrez le fichier HTM.  
  
 Vous avez ajouté du code VBScript qui obtiennent la propriété côtés du contrôle et augmente le nombre des côtés d’une unité si vous cliquez à l’intérieur du contrôle. Si vous cliquez en dehors du contrôle, vous réduisez le nombre des côtés d’une unité.  
  
## <a name="indicating-that-the-control-is-safe-for-scripting"></a>Qui indique que le contrôle est sécurisé pour le script  
 Vous pouvez afficher la page Web avec le contrôle dans Internet Explorer, ou plus pour des raisons pratiques, utilisent le navigateur Web intégré à Visual C++. Pour voir votre contrôle dans la vue du navigateur Web, cliquez sur PolyCtl.htm, puis cliquez sur **afficher dans le navigateur**.  
  
 Selon les paramètres de sécurité Internet Explorer, vous pouvez recevoir une boîte de dialogue indiquant que le contrôle peut ne pas être sécurisé pour les scripts et peut potentiellement endommager d’alerte de sécurité. Par exemple, si vous aviez un contrôle qui affiche un fichier, mais a également un `Delete` méthode qui a supprimé un fichier, il est recommandé si vous venez de le visualiser sur une page. Il serait pas fiable générer un script, toutefois, étant donné que quelqu'un pourrait appeler le `Delete` (méthode).  
  
> [!IMPORTANT]
>  Pour ce didacticiel, vous pouvez modifier vos paramètres de sécurité dans Internet Explorer pour exécuter les contrôles ActiveX qui ne sont pas marqués comme sécurisés. Dans le panneau de configuration, cliquez sur **propriétés Internet** et cliquez sur **sécurité** pour modifier les paramètres appropriés. Lorsque vous avez terminé le didacticiel, modifiez vos paramètres de sécurité à leur état d’origine.  
  
 Vous pouvez par programmation avertir Internet Explorer pour qu’il est inutile afficher la boîte de dialogue Alerte de sécurité pour ce contrôle particulier. Vous pouvez faire avec le `IObjectSafety` interface et ATL fournit une implémentation de cette interface dans la classe [IObjectSafetyImpl](../atl/reference/iobjectsafetyimpl-class.md). Pour ajouter l’interface à votre contrôle, ajoutez `IObjectSafetyImpl` à votre liste de classes héritées et ajoutez-lui une entrée dans votre mappage COM.  
  
#### <a name="to-add-iobjectsafetyimpl-to-the-control"></a>Pour ajouter IObjectSafetyImpl au contrôle  
  
1.  Ajoutez la ligne suivante à la fin de la liste des classes héritées dans PolyCtl.h et ajoutez une virgule à la ligne précédente :  
  
 [!code-cpp[NVC_ATL_Windowing#62](../atl/codesnippet/cpp/putting-the-control-on-a-web-page-atl-tutorial-part-7_1.h)]  
  
2.  Ajoutez la ligne suivante au mappage COM dans PolyCtl.h :  
  
 [!code-cpp[NVC_ATL_Windowing#63](../atl/codesnippet/cpp/putting-the-control-on-a-web-page-atl-tutorial-part-7_2.h)]  
  
## <a name="building-and-testing-the-control"></a>Génération et test du contrôle  
 Générer le contrôle. Une fois la build terminée, ouvrez à nouveau PolyCtl.htm dans l’affichage du navigateur. Cette fois, la page Web doit être affichée directement sans la boîte de dialogue Alerte de sécurité. Cliquez à l’intérieur du polygone ; le nombre de côtés augmente d’un. Cliquez à l’extérieur du polygone pour diminuer le nombre de côtés. Si vous essayez de réduire le nombre de côtés inférieur à trois, vous verrez le message d’erreur que vous définissez.  
  
 [À l’étape 6](../atl/adding-a-property-page-atl-tutorial-part-6.md)  
  
## <a name="next-steps"></a>Étapes suivantes  
 Cela conclut le didacticiel ATL. Pour obtenir des liens vers d’autres informations à propos d’ATL, consultez la [page de démarrage ATL](../atl/active-template-library-atl-concepts.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiel](../atl/active-template-library-atl-tutorial.md)

