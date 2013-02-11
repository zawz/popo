// zamjena A iz C sa znakovima iz B na pritisak tipke

 private void txtTextC_KeyPress(object sender, KeyPressEventArgs e)
        {
            //Provjera da li postoji unos u polja A i B i da li polje C sadrži znakove iz polja A
            if (txtTextA.Text.Length > 0 && txtTextB.Text.Length > 0 && txtTextC.Text.Contains(txtTextA.Text))
            {
                //Zamijeni znakove određene poljem A u polju C s znakovima iz polja B
                txtTextC.Text = txtTextC.Text.Replace(txtTextA.Text, txtTextB.Text);
                //postovi kurosr za pisanje na kraj polja C
                txtTextC.Select(txtTextC.TextLength, 0);
            }           
        }
        
// provjera znaka, zmajena znaka
//kada korisnik pritisne neku tipku
        private void textBox1_KeyPress(object sender, KeyPressEventArgs e)
        {
            //provjerava ako polje sadrži znak a
            if(textBox1.Text.Contains('a'))
            {
                //zamjenjuje znak a s znakom b
                textBox1.Text=textBox1.Text.Replace('a','b');
                //seli kursor za unos na kraj polja, kad ovo nebi stavili onda bi se kursor za unos postavio na početak polja
                textBox1.Select(textBox1.TextLength, 0);
            }
        }
        
