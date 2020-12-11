---
description: 'En savoir plus sur : placer le contrôle sur une page Web (Didacticiel ATL, partie 7)'
title: Insertion d'un contrôle sur une page Web (Didacticiel ATL, Partie 7)
ms.custom: get-started-article
ms.date: 05/06/2019
ms.assetid: 50dc4c95-c95b-4006-b88a-9826f7bdb222
ms.openlocfilehash: 738d847a6436a2afab2e336502ec3255d1a1e589
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97159177"
---
# <a name="putting-the-control-on-a-web-page-atl-tutorial-part-7"></a>Insertion d'un contrôle sur une page Web (Didacticiel ATL, Partie 7)

Votre contrôle est maintenant terminé. Pour voir votre contrôle fonctionner dans une situation réelle, placez-le sur une page Web. Un fichier HTML qui contient le contrôle a été créé lorsque vous avez défini votre contrôle. Ouvrez le fichier PolyCtl.htm à partir de **Explorateur de solutions** et vous pouvez voir votre contrôle sur une page Web.

Au cours de cette étape, vous allez ajouter des fonctionnalités au contrôle et générer un script de la page Web pour répondre aux événements. Vous allez également modifier le contrôle pour permettre à Internet Explorer de reconnaître que le contrôle est sécurisé pour l’écriture de scripts.

## <a name="adding-new-functionality"></a>Ajout de nouvelles fonctionnalités

### <a name="to-add-control-features"></a>Pour ajouter des fonctionnalités de contrôle

1. Ouvrez PolyCtl. cpp et remplacez le code suivant :

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

La forme va à présent ajouter ou supprimer des côtés en fonction de l’endroit où vous cliquez.

## <a name="scripting-the-web-page"></a>Script de la page Web

Le contrôle n’a pas encore fait quoi que ce soit, modifiez la page Web pour répondre aux événements que vous envoyez.

### <a name="to-script-the-web-page"></a>Pour générer un script de la page Web

1. Ouvrez PolyCtl.htm et sélectionnez affichage HTML. Ajoutez les lignes suivantes au code HTML. Ils doivent être ajoutés après `</OBJECT>` mais avant `</BODY>` .

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

Vous avez ajouté du code VBScript qui obtient la propriété Sides à partir du contrôle. Il augmente le nombre de côtés d’un si vous cliquez à l’intérieur du contrôle. Si vous cliquez en dehors du contrôle, vous réduisez le nombre de côtés d’un.

## <a name="indicating-that-the-control-is-safe-for-scripting"></a>Indiquant que le contrôle est sécurisé pour l’écriture de scripts

Vous pouvez afficher la page Web avec le contrôle uniquement dans Internet Explorer. D’autres navigateurs ne prennent plus en charge les contrôles ActiveX en raison de failles de sécurité.

> [!NOTE]
> Si le contrôle n’est pas visible, sachez que certains navigateurs nécessitent des ajustements de paramètres pour exécuter les contrôles ActiveX. Reportez-vous à la documentation du navigateur sur l’activation des contrôles ActiveX.

En fonction des paramètres de sécurité actuels d’Internet Explorer, vous pouvez recevoir une boîte de dialogue d’alerte de sécurité. Elle indique que le contrôle peut ne pas être sûr pour le script et peut potentiellement causer des dommages. Par exemple, si vous disposiez d’un contrôle qui affichait un fichier, mais également d’une `Delete` méthode qui a supprimé un fichier, ce serait sûr si vous venez de l’afficher sur une page. Toutefois, il ne serait pas possible de créer un script sûr, car quelqu’un pouvait appeler la `Delete` méthode.

> [!IMPORTANT]
> Pour ce didacticiel, vous pouvez modifier vos paramètres de sécurité dans Internet Explorer pour exécuter des contrôles ActiveX qui ne sont pas marqués comme sécurisés. Dans le panneau de configuration, cliquez sur **Propriétés Internet** , puis sur **sécurité** pour modifier les paramètres appropriés. Une fois le didacticiel terminé, redéfinissez vos paramètres de sécurité à leur état d’origine.

Vous pouvez alerter par programmation Internet Explorer qu’il n’est pas nécessaire d’afficher la boîte de dialogue alerte de sécurité pour ce contrôle particulier. Vous pouvez le faire à l’aide de l' `IObjectSafety` interface. ATL fournit une implémentation de cette interface dans la classe [IObjectSafetyImpl](../atl/reference/iobjectsafetyimpl-class.md). Pour ajouter l’interface à votre contrôle, ajoutez `IObjectSafetyImpl` à votre liste de classes héritées et ajoutez une entrée pour celle-ci dans votre mappage com.

### <a name="to-add-iobjectsafetyimpl-to-the-control"></a>Pour ajouter IObjectSafetyImpl au contrôle

1. Ajoutez la ligne suivante à la fin de la liste des classes héritées dans PolyCtl. h et ajoutez une virgule à la ligne précédente :

    [!code-cpp[NVC_ATL_Windowing#62](../atl/codesnippet/cpp/putting-the-control-on-a-web-page-atl-tutorial-part-7_1.h)]

1. Ajoutez la ligne suivante à la table COM dans PolyCtl. h :

    [!code-cpp[NVC_ATL_Windowing#63](../atl/codesnippet/cpp/putting-the-control-on-a-web-page-atl-tutorial-part-7_2.h)]

## <a name="building-and-testing-the-control"></a>Création et test du contrôle

Générez le contrôle. Une fois la génération terminée, ouvrez à nouveau PolyCtl.htm dans la vue du navigateur. Cette fois-ci, la page Web doit être affichée directement sans la boîte de dialogue **alerte de sécurité** . Si vous cliquez à l’intérieur du polygone, le nombre de côtés augmente d’une unité. Cliquez en dehors du polygone pour réduire le nombre de côtés.

[Retour à l’étape 6](../atl/adding-a-property-page-atl-tutorial-part-6.md)

## <a name="next-steps"></a>Étapes suivantes

Cette étape conclut le Didacticiel ATL. Pour obtenir des liens vers des informations supplémentaires sur ATL, consultez la [page de démarrage ATL](../atl/active-template-library-atl-concepts.md).

## <a name="see-also"></a>Voir aussi

[Didacticiel](../atl/active-template-library-atl-tutorial.md)
