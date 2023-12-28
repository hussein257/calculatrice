<!DOCTYPE html>
<html>
    <head>
        <title>Calculatrice</title>
    </head>
    <body>
        <?php
            $result=0;
            $a="";
            $b="";
            if(isset($_POST['a']) AND isset($_POST['b']) AND isset($_POST['operation'])){
                if(!empty($_POST['a']) AND !empty($_POST['b'])){
                    $a=$_POST['a'];
                    $b=$_POST['b'];
                    $o=$_POST['operation'];
                    if($o=="addition"){
                        $result=$a+$b;
                    } else if($o=="soustrat"){
                        $result=$a-$b;
                    } else if($o=="multi"){
                        $result=$a*$b;
                    } else if($o=="division"){
                        if($b!=0)
                            $result=$a/$b;
                        else
                            $result="Impossible";
                    } else if($o=="carre"){
                        $result=$a*$a;
                    }
                }else{
                    echo "<p style='color:red;'>Au moins un des paramètres est vide!</p>";
                }
            }else{
                echo "<p style='color:red;'>Au moins un des paramètres n'existe pas!</p>";
            }
        ?>
        <form method="POST" action="" style="border: 2px solid black;">
            <h2>Calculatrice</h2>
            <table>
                <tr>
                    <td>A</td>
                    <td>
                        <input type="text" name="a"  value="<?php echo $a; ?>" placeholder="Taper le 1er nombre">
                    </td><td>B</td>
                    <td>
                        <input type="text" name="b"  value="<?php echo $b; ?>" placeholder="Taper le 2ème nombre">
                    </td>
                </tr>
                <tr>
                    <td colspan="4">
                        <input type="radio" checked="checked" name="operation" value="addition"> +
                        <input type="radio" name="operation" value="soustrat" style="margin-left: 20px;"> -
                        <input type="radio" name="operation" value="multi" style="margin-left: 20px;"> X
                        <input type="radio" name="operation" value="division" style="margin-left: 20px;"> :
                        <input type="radio" name="operation" value="carre" style="margin-left: 20px;"> X<sup>2</sup>
                    </td>
                </tr>
                <tr>
                    <td></td>
                    <td></td><td></td>
                    <td>
                        <input type="submit" value="Calculer">
                    </td>
                </tr>
                <tr>
                    <td colspan="3">Résultat</td>
                    
                    <td>
                        <input type="text" placeholder="Résultat" value="<?php echo $result; ?>">
                    </td>
                </tr>
            </table>
        </form>
    </body>
</html>

