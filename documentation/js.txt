let menu = document.querySelector('#menu-bar');
let navbar = document.querySelector('.navbar');

menu.onclick = () => {
    
    menu.classList.toggle('fa-times');
    navbar.classList.toggle('active');

}

window.onscroll = () => {

    menu.classList.remove('fa-times');
    navbar.classList.remove('active');

    if (window.scrollY > 60) {
        document.querySelector('#scroll-top').classList.add('active');
    } else {
        document.querySelector('#scroll-top').classList.remove('active');
    }

}

// displaying a pop-up with i9tem description start

let items = document.querySelectorAll('.item');

items.forEach((item, a) => {
    item.onclick = function() {
        $('#item-detail').addClass('d-block')
        $('#cancel').click(function() {
            $('#item-detail').removeClass('d-block')
        })

        fetch('item.json').then(response => response.json()).then(json => {
            itemDescription = document.querySelector("#item-description")
            itemName = document.querySelector("#item-name")
            itemprice = document.querySelector("#item-price")
            itemImage = document.querySelector("#item-image")
            itemIngredientKey = document.querySelector("#item-ingredientKey")

            let listHTML = "";
            itemName.innerHTML = json.item_list[a].name
            itemImage.src = json.item_list[a].image
            itemDescription.innerHTML = json.item_list[a].description
            itemprice.innerHTML = ` ${json.item_list[a].price}$ `
            for (let i = 0; i < json.item_list[a].ingredients.key.length; i++) {

                listHTML += `<p>▢ ${json.item_list[a].ingredients.key[i]}.</p>`

            }
            itemIngredientKey.innerHTML = listHTML;
        })
    }
})


// displaying a pop-up with item description ends




// Ratng function starts 



const allstars = document.querySelectorAll('.star')

allstars.forEach((star, i) => {
    
    star.onclick = function() {
        console.log(star)
        let starLevel = i + 1

        allstars.forEach((star, j) => {
            if (starLevel >= j + 1) {
                star.innerHTML = '&#9733';
            } else {
                star.innerHTML = '&#9734'
            }
        })

    }
})



//  function for loading starts


function loader() {
    document.querySelector('.loader-container').classList.add('fade-out');
}

function fadeOut() {
    setInterval(loader, 300);
}

window.onload = fadeOut();

// function for loading ends


// timer functionality

function timer() {
    let date = new Date().getDate();
    let hour = new Date().getHours();
    let mins = new Date().getMinutes();

    let secs = new Date().getSeconds();
    let day = new Date().getDay();
    let month = new Date().getMonth() + 1;
    let session;

    switch (day) {
        case 1:
            day = "monday"
            break;
        case 2:
            day = "tuesday"
            break;
        case 3:
            day = "wednessday"
            break;
        case 4:
            day = "thursday"
            break;
        case 5:
            day = "friday"
            break;
        case 6:
            day = "saturday"
            break;
        case 0:
            day = "sunday"
            break;

    }

    switch (month) {
        case 1:
            month = "january"
            break;
        case 2:
            month = "february"
            break;
        case 3:
            month = "march"
            break;
        case 4:
            month = "april"
            break;
        case 5:
            month = "may"
            break;
        case 6:
            month = "june"
            break;
        case 7:
            month = "july"
            break;

        case 8:
            month = "august"
            break;

        case 9:
            month = "september"
            break;

        case 10:
            month = "october"
            break;

        case 11:
            month = "november"
            break;

        case 12:
            month = "december"
            break;

    }

    if (hour >= 12) {
        session = "pm"
    } else {
        session = "am"
    }

    if (hour > 12) {
        hour = hour - 12
    }

    if (hour < 10) { hour = "0" + hour  } if (mins < 10) { mins = "0" + mins  } if (secs < 10) { secs = "0" + secs  }

    document.querySelector("#date").innerHTML = date;
    document.querySelector("#month").innerHTML = month;
    document.querySelector("#day").innerHTML = day;
    document.querySelector("#hour").innerHTML = hour + ":";
    document.querySelector("#mins").innerHTML = mins + ":";
    document.querySelector("#secs").innerHTML = secs;
    document.querySelector("#session").innerHTML = session;
}
setInterval(timer, 10)




//feedback function starts

const feedback = document.querySelector('#feedback')

feedback.onclick = function(a) {
    a.preventDefault()

    let name = document.querySelector('#name').value
    let email = document.querySelector('#email').value
    let feed = document.querySelector('#feed').value

    if (name != '' && email != '' && feed != '') {
        let feedback = {
            "name": "",
            "email": "",
            "feedback": ""
        }

        feedback.name = name
        feedback.email = email
        feedback.feedback = feed

        alert("Thanks for your feedback")

    } else {
        alert("please fill all input")
    }



}




