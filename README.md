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
        
// slika

private void button1_Click(object sender, EventArgs e)
        {
            if (openFileDialog1.ShowDialog() == DialogResult.OK)
            {
                pictureBox1.Load(openFileDialog1.FileName);
            }
        }
        
        
//na 10 promjena boje

 //kad korisnik klikne na gumb
        private void btnGumb_Click(object sender, EventArgs e)
        {
            //uvećaj varijablu koja broji klikove
            klikova++;

            //ako je broj klikova djeljiv s 10 promjeni boju pozadine u crveno
            if (klikova % 10 == 0)
                this.BackColor = Color.Red;
            //ako nije djeljiv s 10 onda je pozadina forme zelena
            else
                this.BackColor = Color.Green;
            
            //na gumb ispiši broj klikova
            btnGumb.Text = klikova.ToString();
        }
        
//zajednicki elementi

 //kad korisnik klikne na gumb
        private void btnZajednicki_Click(object sender, EventArgs e)
        {
            //varijabla za zajedničke brojeve
            string zajednickiBrojevi="";

            //pretvori unos u string polje, delimiter je zarez
            string[] skupA = txtSkupA.Text.Split(',');
            string[] skupB = txtSkupB.Text.Split(',');

            //za svaki unešeni znak u prvom polju
            for (int i = 0; i < skupA.Length; i++)
            {
                //za svaki unešeni znak u drugom polju
                for (int j = 0; j < skupB.Length; j++)
                {
                    //ako se trenutni znak u polju skupB na poziciji j i znak u polju skupA na poziji i podudaraju, dodaj taj znak u varijablu za zajedničke brojeve
                    if(skupB[j]==skupA[i])
                         zajednickiBrojevi += skupB[j] + ",";
                }  
            }

            //ako postoje zajednički brojevi, onda makni zadnji znak iz stringa za zajedničke brojeve (zadnji znak je zarez)
            if (zajednickiBrojevi.Length > 0)
                zajednickiBrojevi = zajednickiBrojevi.Remove(zajednickiBrojevi.Length - 1);

            //prikaži zajedničke brojeve na formi
            txtSkupC.Text = zajednickiBrojevi;
        }
// boje
int red , green , blue

//ako sva tri polja može pretvoriti u brojeve
            if (int.TryParse(txtRed.Text, out red) && int.TryParse(txtGreen.Text, out green) && int.TryParse(txtBlue.Text, out blue))
            {
                //ako su vrijednosti tih brojeva u intervalu od 0-255
                if ((red >= 0 && red <= 255) && (green >= 0 && green <= 255) && (blue >= 0 && blue <= 255))
                {
                    //promjeni boju forme u boju određenu tim brojevima
                    this.BackColor = Color.FromArgb(red, green, blue);
                    lblStatus.Text = "";
                }
                    //vrijednosti brojeva nisu u intervalu od 0-255
                else
                    lblStatus.Text = "Polja moraju imati vrijednost 0-255";
            }
                //unešeno nije broj
            else
            {
                lblStatus.Text = "Polja nisu broj";
            }            
