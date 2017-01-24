---
title: "Contr&#244;les ActiveX MFC&#160;: optimisation | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "contextes de périphérique, non découpés pour les contrôles ActiveX MFC"
  - "contrôles ActiveX sans scintillement"
  - "contrôles ActiveX MFC, état actif/inactif"
  - "contrôles ActiveX MFC, sans scintillement"
  - "contrôles ActiveX MFC, interaction souris"
  - "contrôles ActiveX MFC, optimiser"
  - "contrôles ActiveX MFC, sans fenêtre"
  - "optimisation, contrôles ActiveX"
  - "optimiser les performances, contrôles ActiveX"
  - "performances, contrôles ActiveX"
  - "contrôles ActiveX MFC sans fenêtre"
ms.assetid: 8b11f26a-190d-469b-b594-5336094a0109
caps.latest.revision: 8
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Contr&#244;les ActiveX MFC&#160;: optimisation
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

This article explains techniques you can use to optimize your ActiveX controls for better performance.  
  
 The topics [Turning Off the Activate When Visible Option](../mfc/turning-off-the-activate-when-visible-option.md) and [Providing Mouse Interaction While Inactive](../mfc/providing-mouse-interaction-while-inactive.md) discuss controls that don't create a window until activated.  The topic [Providing Windowless Activation](../mfc/providing-windowless-activation.md) discusses controls that never create a window, even when they are activated.  
  
 Windows have two major drawbacks for OLE objects: they prevent objects from being transparent or nonrectangular when active, and they add a large overhead to the instantiation and display of controls.  Typically, creating a window takes 60 percent of a control's creation time.  With a single shared window \(usually the container's\) and some dispatching code, a control receives the same window services, generally without a loss of performance.  Having a window is mostly unnecessary overhead for the object.  
  
 Some optimizations do not necessarily improve performance when your control is used in certain containers.  For example, containers released prior to 1996 did not support windowless activation, so implementing this feature will not provide a benefit in older containers.  However, nearly every container supports persistence, so optimizing your control's persistence code will likely improve its performance in any container.  If your control is specifically intended to be used with one particular type of container, you may want to research which of these optimizations is supported by that container.  In general, however, you should try to implement as many of these techniques as are applicable to your particular control to ensure your control performs as well as it possibly can in a wide array of containers.  
  
 You can implement many of these optimizations through the [MFC ActiveX Control Wizard](../mfc/reference/mfc-activex-control-wizard.md), on the [Control Settings](../mfc/reference/control-settings-mfc-activex-control-wizard.md) page.  
  
### MFC ActiveX Control Wizard OLE Optimization Options  
  
|Control setting in the MFC ActiveX Control Wizard|Action|Complément d'information|  
|-------------------------------------------------------|------------|------------------------------|  
|**Activate when visible** check box|Clear|[Turning Off the Activate When Visible Option](../mfc/turning-off-the-activate-when-visible-option.md)|  
|**Windowless activation** check box|Sélectionner|[Providing Windowless Activation](../mfc/providing-windowless-activation.md)|  
|**Unclipped device context** check box|Sélectionner|[Using an Unclipped Device Context](../mfc/using-an-unclipped-device-context.md)|  
|**Flicker\-free activation** check box|Sélectionner|[Providing Flicker\-Free Activation](../mfc/providing-flicker-free-activation.md)|  
|**Mouse pointer notifications when inactive** check box|Sélectionner|[Providing Mouse Interaction While Inactive](../mfc/providing-mouse-interaction-while-inactive.md)|  
|**Optimized drawing code** check box|Sélectionner|[Optimizing Control Drawing](../mfc/optimizing-control-drawing.md)|  
  
 For detailed information about the member functions that implement these optimizations, see [COleControl](../mfc/reference/colecontrol-class.md).  The member functions are listed by use, such as [Windowless Operations](http://msdn.microsoft.com/fr-fr/e9e28f79-9a70-4ae4-a5aa-b3e92f1904df) and [Inactive Pointer Handling Functions](http://msdn.microsoft.com/fr-fr/e9e28f79-9a70-4ae4-a5aa-b3e92f1904df).  
  
 Pour plus d'informations, consultez :  
  
-   [Optimizing Persistence and Initialization](../mfc/optimizing-persistence-and-initialization.md)  
  
-   [Providing Windowless Activation](../mfc/providing-windowless-activation.md)  
  
-   [Turning Off the Activate When Visible Option](../mfc/turning-off-the-activate-when-visible-option.md)  
  
-   [Providing Mouse Interaction While Inactive](../mfc/providing-mouse-interaction-while-inactive.md)  
  
-   [Providing Flicker\-Free Activation](../mfc/providing-flicker-free-activation.md)  
  
-   [Using an Unclipped Device Context](../mfc/using-an-unclipped-device-context.md)  
  
-   [Optimizing Control Drawing](../mfc/optimizing-control-drawing.md)  
  
## Voir aussi  
 [Contrôles ActiveX MFC](../mfc/mfc-activex-controls.md)