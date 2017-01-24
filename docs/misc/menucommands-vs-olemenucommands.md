---
title: "MenuCommands Vs. OleMenuCommands | Microsoft Docs"
ms.custom: ""
ms.date: "11/23/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "commandes, créer dans des VSPackages"
  - "boutons de commande, créer et placer"
  - "menus, créer des commandes"
ms.assetid: 553d5e07-3e19-4aba-b490-6c7dd05fd82e
caps.latest.revision: 46
caps.handback.revision: 46
manager: "douge"
---
# MenuCommands Vs. OleMenuCommands
Vous pouvez créer des commandes de menu en dérivant de <xref:System.ComponentModel.Design.MenuCommand> ou de l’objet <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> et en implémentant les gestionnaires d’événements appropriés. Dans la plupart des cas, vous pouvez utiliser <xref:System.ComponentModel.Design.MenuCommand>, à l’instar du modèle de projet VSPackage, mais vous pouvez parfois être amené à utiliser <xref:Microsoft.VisualStudio.Shell.OleMenuCommand>.  
  
 Les commandes qu’un VSPackage met à la disposition de l’IDE doivent être visibles et activées avant qu’un utilisateur puisse les utiliser. Quand elles sont créées dans un fichier .vsct à l’aide du modèle de projet de package Visual Studio, les commandes sont visibles et activées par défaut. Le fait de définir des indicateurs de commande, tels que `DynamicItemStart`, peut modifier le comportement par défaut. La visibilité, l’état activé et les autres propriétés d’une commande peuvent aussi être modifiés dans le code au moment de l’exécution en accédant à l’objet <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> associé à la commande.  
  
## Composants requis  
 Pour suivre cette procédure pas à pas, vous devez installer le Kit de développement logiciel \(SDK\) Visual Studio. Pour plus d'informations, consultez [Kit de développement logiciel Visual Studio](../Topic/Visual%20Studio%20SDK.md).  
  
## Emplacements du modèle de projet de package Visual Studio  
 Vous pouvez trouver le modèle de package Visual Studio dans la boîte de dialogue **Nouveau projet** sous **Visual Basic \/ Extensibilité**, **C\# \/ Extensibilité** ou **Autres types de projets \/ Extensibilité**.  
  
## Création d’une commande  
 L’ensemble des commandes, groupes de commandes, menus, barres d’outils et fenêtres Outil sont définis dans le fichier .vsct. Pour plus d'informations, consultez [Table de commandes de Visual Studio \(. Fichiers VSCT\)](../Topic/Visual%20Studio%20Command%20Table%20\(.Vsct\)%20Files.md).  
  
 Si vous créez un VSPackage à l’aide du modèle de package, sélectionnez **Commande de menu** pour créer un fichier .vsct et définir une commande de menu par défaut. Pour plus d'informations, consultez [Création d'une Extension avec une commande de Menu](../Topic/Creating%20an%20Extension%20with%20a%20Menu%20Command.md).  
  
#### Pour ajouter une commande à l’IDE  
  
1.  Ouvrez le fichier .vsct.  
  
2.  Dans la section `Symbols`, recherchez l’élément [GuidSymbol](../Topic/GuidSymbol%20Element.md) qui contient les groupes et les commandes.  
  
3.  Créez un élément [IDSymbol](../Topic/IDSymbol%20Element.md) pour chaque menu, groupe ou commande à ajouter, comme le montre l’exemple suivant.  
  
     [!CODE [ButtonGroup#01](../CodeSnippet/VS_Snippets_VSSDK/buttongroup#01)]  
  
     Les attributs `name` des éléments `GuidSymbol` et `IDSymbol` fournissent la paire GUID:ID pour chaque nouveau menu, groupe ou commande. Le `guid` représente un jeu de commandes défini pour votre VSPackage. Vous pouvez définir plusieurs jeux de commandes. Chaque paire GUID:ID doit être unique.  
  
4.  Dans la section [Buttons](../Topic/Buttons%20Element.md), créez un élément [Button](../Topic/Button%20Element.md) pour définir la commande, comme le montre l’exemple suivant.  
  
     [!CODE [ButtonGroup#03](../CodeSnippet/VS_Snippets_VSSDK/buttongroup#03)]  
  
    1.  Définissez les champs `guid` et `id` de façon à les faire correspondre à la paire GUID:ID de la nouvelle commande.  
  
    2.  Définissez l’attribut `priority`.  
  
         L’attribut `priority` est utilisé par le fichier .vsct pour déterminer l’emplacement du bouton parmi les autres objets présents dans son groupe parent.  
  
         Les commandes qui ont des valeurs de priorité inférieure s’affichent au\-dessus ou à gauche des commandes qui ont des valeurs de priorité plus élevées. Les valeurs de priorité en double sont autorisées, mais la position relative des commandes de même priorité est déterminée par l’ordre de traitement des VSPackages au moment de l’exécution, et cet ordre ne peut pas être prédéterminé.  
  
         Si vous omettez l’attribut `priority`, la valeur 0 lui est affectée.  
  
    3.  Définissez l’attribut `type`. Dans la plupart des cas, sa valeur est `"Button"`. Pour obtenir une description des autres types de boutons valides, consultez [Élément de bouton](../Topic/Button%20Element.md).  
  
5.  Dans la définition du bouton, créez un élément [Strings](../Topic/Strings%20Element.md) contenant un élément [ButtonText](../Topic/ButtonText%20Element.md). Celui\-ci contiendra le nom du menu tel qu’il apparaîtra dans l’IDE. Créez ensuite un élément [CommandName](../Topic/CommandName%20Element.md) qui contiendra le nom de la commande utilisé pour accéder au menu de la fenêtre **Commande**.  
  
     Si la chaîne de texte du bouton inclut le caractère « & », l’utilisateur peut ouvrir le menu en appuyant sur ALT puis sur le caractère qui suit « & ».  
  
     L’ajout d’un élément `Tooltip` fait apparaître le texte qu’il contient quand un utilisateur place le pointeur sur le bouton.  
  
6.  Ajoutez un élément [Icon](../Topic/Icon%20Element.md) pour spécifier l’icône éventuelle à afficher avec la commande. Si les icônes sont obligatoires pour les boutons des barres d’outils, elles ne le sont pas pour les éléments de menu. Le `guid` et l’`id` de l’élément `Icon` doivent correspondre à ceux d’un élément [Bitmap](../Topic/Bitmap%20Element.md) défini dans la section `Bitmaps`.  
  
7.  Ajoutez des indicateurs de commande, si nécessaire, pour modifier l’apparence et le comportement du bouton. Pour ce faire, ajoutez un élément [CommandFlag](../Topic/Command%20Flag%20Element.md) dans la définition du menu.  
  
8.  Définissez le groupe parent de la commande. Le groupe parent peut être un groupe que vous créez, un groupe d’un autre package ou un groupe de l’IDE. Par exemple, pour ajouter votre commande à la barre d’outils d’édition de Visual Studio, à côté des boutons **Commentaire** et **Supprimer le commentaire**, attribuez au parent la valeur guidStdEditor:IDG\_VS\_EDITTOOLBAR\_COMMENT. Si le parent est un groupe défini par l’utilisateur, il doit être l’enfant d’un menu, d’une barre d’outils ou d’une fenêtre Outil qui apparaît dans l’IDE.  
  
     Pour cela, vous pouvez procéder de deux manières différentes, qui dépendent de votre conception :  
  
    -   Dans l’élément `Button`, créez un élément [Parent](../Topic/Parent%20Element.md) et attribuez à ses champs `guid` et `id` la valeur de Guid et d’ID du groupe appelé à héberger la commande, aussi appelé *groupe parent principal*.  
  
         L’exemple suivant définit une commande destinée à figurer dans un menu défini par l’utilisateur.  
  
         [!CODE [TopLevelMenu#03](../CodeSnippet/VS_Snippets_VSSDK/toplevelmenu#03)]  
  
    -   Vous pouvez omettre l’élément `Parent` si la commande doit être positionnée en utilisant le placement de commande. Créez un élément [CommandPlacements](../Topic/CommandPlacements%20Element.md) avant la section `Symbols`, puis ajoutez un élément [CommandPlacement](../Topic/CommandPlacement%20Element.md) ayant le `guid` et l’`id` de la commande, une priorité \(`priority`\) et un parent, comme l’illustre l’exemple suivant.  
  
         [!CODE [ButtonGroup#04](../CodeSnippet/VS_Snippets_VSSDK/buttongroup#04)]  
  
         Si vous créez plusieurs placements de commandes et que leur paire GUID:ID est identique mais pas les parents, le menu apparaît à plusieurs endroits. Pour plus d’informations, consultez l’élément [CommandPlacements](../Topic/CommandPlacements%20Element.md).  
  
     Pour plus d’informations sur les groupes de commandes et le parentage, consultez [Création de groupes de boutons réutilisables](../Topic/Creating%20Reusable%20Groups%20of%20Buttons.md).  
  
 À ce stade, la commande est visible dans l’IDE, mais elle n’a aucune fonctionnalité. Si la commande a été créée par le modèle de package, par défaut, elle a un gestionnaire de clics qui affiche un message.  
  
## Gestion de la nouvelle commande  
 La plupart des commandes présentes dans du code managé peuvent être gérées par MPF \(Managed Package Framework\) en les associant à un objet <xref:System.ComponentModel.Design.MenuCommand> ou <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> et en implémentant leurs gestionnaires d’événements.  
  
 Pour le code qui utilise directement l’interface <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> pour la gestion des commandes, vous devez implémenter l’interface <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> et ses méthodes. Les deux méthodes les plus importants sont <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> et <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A>.  
  
1.  Obtenez l’instance de <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService>, comme le montre l’exemple suivant.  
  
     [!code-cs[ButtonGroup#21](../misc/codesnippet/CSharp/menucommands-vs-olemenucommands_5.cs)]  
  
2.  Créez un objet <xref:System.ComponentModel.Design.CommandID> ayant pour paramètres le GUID et l’ID de la commande à gérer, comme le montre l’exemple suivant.  
  
     [!code-cs[ButtonGroup#22](../misc/codesnippet/CSharp/menucommands-vs-olemenucommands_6.cs)]  
  
     Le modèle de package Visual Studio fournit deux collections, `GuidList` et `PkgCmdIDList`, pour conserver les GUID et ID de commandes. Ceux\-ci sont remplis automatiquement pour les commandes ajoutées par le modèle. En revanche, pour les commandes que vous ajoutez manuellement, vous devez aussi ajouter l’entrée d’ID à la classe `PkgCmdIdList`.  
  
     Une autre solution consiste à remplir l’objet <xref:System.ComponentModel.Design.CommandID> en utilisant la valeur de chaîne brute du GUID et la valeur entière de l’ID.  
  
3.  Instanciez un objet <xref:System.ComponentModel.Design.MenuCommand> ou <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> qui spécifie la méthode chargée de gérer la commande en même temps que le <xref:System.ComponentModel.Design.CommandID>, comme l’illustre l’exemple suivant.  
  
     [!code-cs[ButtonGroup#23](../misc/codesnippet/CSharp/menucommands-vs-olemenucommands_7.cs)]  
  
     L’objet <xref:System.ComponentModel.Design.MenuCommand> est tout indiqué pour les commandes statiques. L’affichage des éléments de menu dynamique nécessite des gestionnaires d’événements QueryStatus. L’objet <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> ajoute l’événement <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus>, qui se produit quand le menu hôte de la commande est ouvert, ainsi que d’autres propriétés, telles que <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.Text%2A>.  
  
     Les commandes créées par le modèle de package sont passés par défaut à un objet <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> dans la méthode `Initialize()` de la classe de package.  
  
4.  L’objet <xref:System.ComponentModel.Design.MenuCommand> est tout indiqué pour les commandes statiques. L’affichage des éléments de menu dynamique nécessite des gestionnaires d’événements QueryStatus. L’objet <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> ajoute l’événement <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus>, qui se produit quand le menu hôte de la commande est ouvert, ainsi que d’autres propriétés, telles que <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.Text%2A>.  
  
     Les commandes créées par le modèle de package sont passés par défaut à un objet <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> dans la méthode `Initialize()` de la classe de package. L’Assistant de Visual Studio implémente la méthode `Initialize` en utilisant `MenuCommand`. Pour l’affichage des éléments de menu dynamique, vous devez remplacer ce dernier par `OleMenuCommand`, comme indiqué dans l’étape suivante. De plus, pour modifier le texte d’un élément de menu, vous devez ajouter un indicateur de commande TextChanges au bouton de commande de menu dans le fichier .vsct, comme le montre l’exemple suivant.  
  
     [!CODE [MenuText#02](../CodeSnippet/VS_Snippets_VSSDK/menutext#02)]  
  
5.  Passez la nouvelle commande de menu à la méthode <xref:System.ComponentModel.Design.IMenuCommandService.AddCommand%2A> de l’interface <xref:System.ComponentModel.Design.IMenuCommandService>. Cette tâche s’exécute par défaut pour les commandes créées par le modèle de package, comme l’illustre l’exemple suivant.  
  
     [!code-cs[ButtonGroup#24](../misc/codesnippet/CSharp/menucommands-vs-olemenucommands_9.cs)]  
  
6.  Implémentez la méthode qui gère la commande.  
  
#### Pour implémenter QueryStatus  
  
1.  L’événement QueryStatus se produit avant l’affichage d’une commande. Les propriétés de cette commande peuvent ainsi être définies dans le gestionnaire d’événements avant d’atteindre l’utilisateur. Seules les commandes ajoutées en tant qu’objets <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> peuvent accéder à cette méthode.  
  
     Ajoutez un objet `EventHandler` à l’événement <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> de l’objet <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> qui est créé pour gérer la commande, comme le montre l’exemple suivant \(`menuItem` est l’instance de <xref:Microsoft.VisualStudio.Shell.OleMenuCommand>\).  
  
     [!code-cs[MenuText#14](../misc/codesnippet/CSharp/menucommands-vs-olemenucommands_10.cs)]
     [!code-vb[MenuText#14](../misc/codesnippet/VisualBasic/menucommands-vs-olemenucommands_10.vb)]  
  
     L’objet `EventHandler` se voit attribuer le nom d’une méthode qui est appelée quand l’état de la commande de menu est demandé.  
  
2.  Implémentez la méthode de gestionnaire de demande d’état pour la commande. Le paramètre `object` `sender` peut faire l’objet d’une conversion de type \(transtypage\) et être converti en objet <xref:Microsoft.VisualStudio.Shell.OleMenuCommand>, qui sert à définir les différents attributs de la commande de menu, y compris le texte. Le tableau suivant présente les propriétés de la classe <xref:System.ComponentModel.Design.MenuCommand> \(dont est dérivée la classe MPF <xref:Microsoft.VisualStudio.Shell.OleMenuCommand>\) qui correspondent aux indicateurs <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>.  
  
    |Propriété MenuCommand|Indicateur OLECMDF|  
    |---------------------------|------------------------|  
    |<xref:System.ComponentModel.Design.MenuCommand.Checked%2A> \= `true`|<xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>|  
    |<xref:System.ComponentModel.Design.MenuCommand.Visible%2A> \= `false`|<xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>|  
    |<xref:System.ComponentModel.Design.MenuCommand.Enabled%2A> \= `true`|<xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>|  
  
     Pour modifier le texte d’une commande de menu, utilisez la propriété <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.Text%2A> de l’objet <xref:Microsoft.VisualStudio.Shell.OleMenuCommand>, comme l’illustre l’exemple suivant.  
  
     [!code-cs[MenuText#11](../misc/codesnippet/CSharp/menucommands-vs-olemenucommands_11.cs)]
     [!code-vb[MenuText#11](../misc/codesnippet/VisualBasic/menucommands-vs-olemenucommands_11.vb)]  
  
 MPF gère automatiquement le cas des groupes non pris en charge ou inconnus. À moins qu’une commande ait été ajoutée à <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> à l’aide de la méthode <xref:System.ComponentModel.Design.IMenuCommandService.AddCommand%2A>, la commande n’est pas prise en charge.  
  
### Gestion des commandes à l’aide de l’interface IOleCommandTarget  
 Pour le code qui utilise directement l’interface <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>, le VSPackage doit implémenter les méthodes <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> et <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> de l’interface <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>. Si le VSPackage implémente une hiérarchie de projet, les méthodes <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> et <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A> de l’interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> doivent être implémentées à leur place.  
  
 Les méthodes <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> et <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> ont toutes deux été conçues pour recevoir un seul `GUID` de jeu de commandes et un tableau d’ID de commandes en entrée. Il est préférable que les VSPackages prennent entièrement en charge ce concept d’ID multiples dans un même appel. Cependant, tant qu’un VSPackage n’est pas appelé à partir d’autres packages VS, vous pouvez considérer que le tableau de commandes ne contient qu’un seul ID de commande, car les méthodes <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> et <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> sont exécutées dans un ordre bien défini. Pour plus d’informations sur le routage, consultez [Routage des commandes dans les packages VS](../Topic/Command%20Routing%20in%20VSPackages.md).  
  
 Pour le code qui utilise directement l’interface <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> pour la gestion des commandes, vous devez implémenter la méthode <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> dans le VSPackage comme indiqué ci\-dessous pour gérer les commandes.  
  
##### Pour implémenter la méthode QueryStatus  
  
1.  Retournez <xref:Microsoft.VisualStudio.VSConstants.S_OK> pour les commandes valides.  
  
2.  Définissez l’élément `cmdf` du paramètre `prgCmds`.  
  
     La valeur de l’élément `cmdf` est l’union logique des valeurs de l’énumération <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>, combinées à l’aide de l’opérateur logique OR \(`|`\).  
  
     Utilisez l’énumération appropriée, en fonction de l’état de la commande :  
  
    -   Si la commande est prise en charge :  
  
         `prgCmds[0].cmdf = OLECMDF_SUPPORTED;`  
  
    -   Si la commande doit être invisible pour le moment :  
  
         `prgCmds[0].cmdf |= OLECMDF_INVISIBLE;`  
  
    -   Si la commande est activée et que l’utilisateur a cliqué dessus :  
  
         `prgCmds[0].cmdf |= OLECMDF_LATCHED;`  
  
         Dans le cas du traitement de commandes hébergées dans un menu de type `MenuControllerLatched`, la première commande à être marquée par l’indicateur `OLECMDF_LATCHED` est la commande par défaut que le menu affiche au démarrage. Pour plus d’informations sur les `MenuController`types de menus, consultez [Élément de menu](../Topic/Menu%20Element.md).  
  
    -   Si la commande est actuellement activée :  
  
         `prgCmds[0].cmdf |= OLECMDF_ENABLED;`  
  
    -   Si la commande fait partie d’un menu contextuel et est masquée par défaut :  
  
         `prgCmds[0] cmdf |= OLECMDF_DEFHIDEONCTXMENU`  
  
    -   Si la commande utilise l’indicateur `TEXTCHANGES`, affectez à l’élément `rgwz` du paramètre `pCmdText` le nouveau texte de la commande et affectez à l’élément `cwActual` du paramètre `pCmdText` la taille de la chaîne de commande.  
  
     Pour les conditions d’erreur, la méthode <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> doit gérer les cas d’erreur suivants :  
  
    -   Si le GUID est inconnu ou non pris en charge, retournez `OLECMDERR_E_UNKNOWNGROUP`.  
  
    -   Si le GUID est connu, mais que l’ID de commande est inconnu ou non pris en charge, retournez `OLECMDERR_E_NOTSUPPORTED`.  
  
 L’implémentation VSPackage de la méthode <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> doit aussi retourner des codes d’erreur spécifiques, selon que la commande est prise en charge et qu’elle a été gérée correctement.  
  
##### Pour implémenter la méthode Exec  
  
-   Si la commande `GUID` est inconnue, retournez `OLECMDERR_E_UNKNOWNGROUP`.  
  
-   Si le `GUID` est connu, mais que l’ID de commande est inconnu, retournez `OLECMDERR_E_NOTSUPPORTED`.  
  
-   Si le `GUID` et l’ID de commande correspond à la paire GUID:ID utilisée par la commande dans le fichier .vsct, exécutez le code associé à la commande et retournez <xref:Microsoft.VisualStudio.VSConstants.S_OK>.  
  
## Voir aussi  
 [Référence de schéma XML de VSCT](../Topic/VSCT%20XML%20Schema%20Reference.md)   
 [Extension des Menus et commandes](../Topic/Extending%20Menus%20and%20Commands.md)