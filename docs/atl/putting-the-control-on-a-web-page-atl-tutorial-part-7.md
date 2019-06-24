---
title: Insertion d'un contrôle sur une page Web (Didacticiel ATL, Partie 7)
ms.custom: get-started-article
ms.date: 05/06/2019
ms.assetid: 50dc4c95-c95b-4006-b88a-9826f7bdb222
ms.openlocfilehash: db6dcc57ff9f3748d802e76617ef18dea8f9506c
ms.sourcegitcommit: 6cf0c67acce633b07ff31b56cebd5de3218fd733
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/24/2019
ms.locfileid: "67344354"
---
# <a name="putting-the-control-on-a-web-page-atl-tutorial-part-7"></a>Insertion d'un contrôle sur une page Web (Didacticiel ATL, Partie 7)

Votre contrôle est maintenant terminé. Pour voir votre contrôle fonctionne dans une situation réelle, vous devez le placer sur une page Web. Un fichier HTML qui contient le contrôle a été créé lorsque vous avez défini votre contrôle. Ouvrez le fichier PolyCtl.htm dans **l’Explorateur de solutions**, et vous pouvez voir votre contrôle sur une page Web.

Dans cette étape, vous allez ajouter des fonctionnalités au contrôle et la page Web pour répondre aux événements de script. Vous allez également modifier le contrôle pour informer Internet Explorer que le contrôle est sécurisé pour le script.

## <a name="adding-new-functionality"></a>Ajouter une nouvelle fonctionnalité

### <a name="to-add-control-features"></a>Pour ajouter des fonctionnalités de contrôle

1. Ouvrez PolyCtl.cpp et remplacez le code suivant :

    ```cpp
    if (PtInRegion(hRgn, xPos, yPos))
        Fire_ClickIn(xPos, yPos);
    else
        Fire_ClickOut(xPos, yPos);
    ```

    par

    ```cpp
    short temp = m_nSides;
    if (PtInRegion(hRgn, xPos, yPos))
    {
        Fire_ClickIn(xPos, yPos);
        put_Sides(++temp);
    }
    else
    {
        Fire_ClickOut(xPos, yPos);
        put_Sides(--temp);
    }
    ```

La forme sera maintenant ajouter ou supprimer les côtés selon l’endroit où vous cliquez.

## <a name="scripting-the-web-page"></a>Script de la Page Web

Le contrôle ne fait rien encore, donc modifier la page Web pour répondre aux événements que vous envoyez.

### <a name="to-script-the-web-page"></a>Créer un script de la page Web

1. Ouvrez PolyCtl.htm et sélectionnez le mode HTML. Ajoutez les lignes suivantes au code HTML. Elles doivent être ajoutées après `</OBJECT>` , mais avant `</BODY>`.

    ```html
    <SCRIPT LANGUAGE="VBScript">
    <!--
        Sub PolyCtl_ClickIn(x, y)
            MsgBox("Clicked (" & x & ", " & y & ") - adding side")
        End Sub
        Sub PolyCtl_ClickOut(x, y)
            MsgBox("Clicked (" & x & ", " & y & ") - removing side")
        End Sub
    -->
    </SCRIPT>
    ```

1. Enregistrez le fichier HTM.

Vous avez ajouté du code VBScript qui obtient la propriété Sides à partir du contrôle. Elle augmente le nombre de côtés d’une unité si vous cliquez à l’intérieur du contrôle. Si vous cliquez en dehors du contrôle, vous réduisez le nombre de côtés d’une unité.

## <a name="indicating-that-the-control-is-safe-for-scripting"></a>Qui indique que le contrôle est sécurisé pour le script

Vous pouvez afficher la page Web avec le contrôle dans Internet Explorer uniquement. D’autres navigateurs ne plus en charge les contrôles ActiveX en raison de failles de sécurité.

> [!NOTE]
> Si le contrôle n’est pas visible, savoir que certains navigateurs nécessitent des réglages de paramètres pour exécuter les contrôles ActiveX. Reportez-vous à la documentation du navigateur sur l’activation des contrôles ActiveX.

Selon les paramètres de sécurité Internet Explorer, vous pouvez recevoir une boîte de dialogue Alerte de sécurité. Elle indique que le contrôle peut ne pas être sûr pour le script et causer des dommages. Par exemple, si vous aviez un contrôle qui affichait un fichier, mais comportait également un `Delete` méthode qui supprimait un fichier, il est possible si vous venez de le visualiser sur une page. Il n’est pas possible générer un script, toutefois, étant donné que quelqu'un pourrait appeler le `Delete` (méthode).

> [!IMPORTANT]
> Pour ce didacticiel, vous pouvez modifier vos paramètres de sécurité d’Internet Explorer pour exécuter les contrôles ActiveX qui ne sont pas marqués comme sécurisés. Dans le panneau de configuration, cliquez sur **propriétés Internet** et cliquez sur **sécurité** pour modifier les paramètres appropriés. Lorsque vous avez terminé le didacticiel, modifiez vos paramètres de sécurité à leur état d’origine.

Vous pouvez par programmation avertir Internet Explorer qu’il n’a pas besoin d’afficher la boîte de dialogue Alerte de sécurité pour ce contrôle. Vous pouvez le faire à l’aide de la `IObjectSafety` interface. ATL fournit une implémentation de cette interface dans la classe [IObjectSafetyImpl](../atl/reference/iobjectsafetyimpl-class.md). Pour ajouter l’interface à votre contrôle, ajoutez `IObjectSafetyImpl` à votre liste des classes héritées et ajoutez une entrée pour elle dans votre mappage COM.

### <a name="to-add-iobjectsafetyimpl-to-the-control"></a>Pour ajouter IObjectSafetyImpl au contrôle

1. Ajoutez la ligne suivante à la fin de la liste des classes héritées dans PolyCtl.h et ajoutez une virgule à la ligne précédente :

    [!code-cpp[NVC_ATL_Windowing#62](../atl/codesnippet/cpp/putting-the-control-on-a-web-page-atl-tutorial-part-7_1.h)]

1. Ajoutez la ligne suivante au mappage COM dans PolyCtl.h :

    [!code-cpp[NVC_ATL_Windowing#63](../atl/codesnippet/cpp/putting-the-control-on-a-web-page-atl-tutorial-part-7_2.h)]

## <a name="building-and-testing-the-control"></a>Création et test du contrôle

Générer le contrôle. Une fois la build terminée, rouvrez PolyCtl.htm dans l’affichage du navigateur. Cette fois, la page Web doit être affichée directement sans le **l’alerte de sécurité** boîte de dialogue. Si vous cliquez à l’intérieur du polygone, le nombre de côtés augmente d’une unité. Cliquez à l’extérieur du polygone pour réduire le nombre de côtés.

[À l’étape 6](../atl/adding-a-property-page-atl-tutorial-part-6.md)

## <a name="next-steps"></a>Étapes suivantes

Cette étape conclut le didacticiel ATL. Pour obtenir des liens vers d’autres informations à propos d’ATL, consultez le [page de démarrage ATL](../atl/active-template-library-atl-concepts.md).

## <a name="see-also"></a>Voir aussi

[Tutoriel](../atl/active-template-library-atl-tutorial.md)
