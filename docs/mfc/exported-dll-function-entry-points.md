---
title: Points d'entrée de fonction DLL exportée
ms.date: 11/04/2016
helpviewer_keywords:
- exporting DLLs [MFC], functions
- MFC, managing state data
- state management [MFC], exported DLLs
ms.assetid: 3268666e-d24b-44f2-80e8-7c80f73b93ca
ms.openlocfilehash: c521cad666864c728fd871b460cf0c92b815e414
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84622639"
---
# <a name="exported-dll-function-entry-points"></a>Points d'entrée de fonction DLL exportée

Pour les fonctions exportées d’une DLL, utilisez la macro [AFX_MANAGE_STATE](reference/extension-dll-macros.md#afx_manage_state) pour conserver l’état global approprié lors du passage du module dll à la dll de l’application appelante.

En cas d'appel, cette macro définit `pModuleState`, un pointeur vers une structure `AFX_MODULE_STATE` contenant des données globales du module, comme l'état du module efficace pour le reste de l'étendue contenante de la fonction. En sortant de l'étendue contenant la macro, l'état du module effectif précédent est automatiquement restauré.

Ce basculement est effectué en construisant une instance d’une `AFX_MODULE_STATE` classe sur la pile. Dans le constructeur, cette classe obtient un pointeur vers l'état du module en cours et l'enregistre dans un attribut, puis définit `pModuleState` comme nouvel état du module effectif. Dans le destructeur, cette classe restaure le pointeur stocké dans une variable membre en tant qu'état du module effectif.

Si vous avez une fonction exportée, telle qu'une fonction qui affiche une boîte de dialogue dans votre DLL, vous devez ajouter le code suivant au début de la fonction :

[!code-cpp[NVC_MFCConnectionPoints#6](codesnippet/cpp/exported-dll-function-entry-points_1.cpp)]

Cela permute l’état du module actuel avec l’état retourné par [AfxGetStaticModuleState](reference/extension-dll-macros.md#afxgetstaticmodulestate) jusqu’à la fin de la portée actuelle.

Les problèmes avec des ressources dans les DLL se poseront si la macro `AFX_MANAGE_STATE` n'est pas utilisée. Par défaut, MFC utilise le handle de ressource d'application principale pour charger le modèle de ressources. Ce modèle est réellement enregistré dans la DLL. La cause racine est que les informations d’état du module MFC n’ont pas été basculées par la macro `AFX_MANAGE_STATE`. Le handle de ressources est récupéré de l'état du module MFC. Ne pas afficher l'état du module provoque l'utilisation du mauvais handle de ressource.

`AFX_MANAGE_STATE` n'a pas besoin d'être placé dans chaque fonction de la DLL. Par exemple, `InitInstance` peut être appelé par du code MFC dans l'application sans `AFX_MANAGE_STATE` car MFC déplace automatiquement l'état du module avant `InitInstance`, puis le restaure après le retour de `InitInstance`. Il en va de même pour tous les gestionnaires de table des messages. Les DLL MFC normales disposent en fait d’une procédure de fenêtre principale spéciale qui change automatiquement l’état du module avant de router les messages.

## <a name="see-also"></a>Voir aussi

[Gestion des données d’état des modules MFC](managing-the-state-data-of-mfc-modules.md)
