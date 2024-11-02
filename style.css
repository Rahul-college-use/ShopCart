let item_name = document.querySelector('#item_name');
let price = document.querySelector('#price');
let addBtn = document.querySelector('#add');
let clearBtn = document.querySelector('#clear');
let add_item_box = document.querySelector('.add_items');
let add_item = document.querySelector('#add_items');
let total_price = document.querySelector('#total_price');
let sum = 0
let pay=document.querySelector('#pay')
// console.log(add_item); // Check if add_item is not null

addBtn.addEventListener('click', () => {

    if (item_name.value != '' && price.value != '') {
        let newDiv = document.createElement('ul');
        add_item_box.style.display = 'block'
        newDiv.style.margin = '1vmax';
        newDiv.innerText = item_name.value;

        // Insert newDiv before add_item if add_item exists
        if (add_item && add_item.parentNode) {
            add_item.parentNode.insertBefore(newDiv, add_item);
        } else {
            console.error("add_item or its parentNode is not found.");
        }



        sum += parseInt(price.value); // Handle any invalid price input as 0
        total_price.innerText = sum;
        item_name.value = ''
        price.value = ''

        let clear = () => {
            console.log("clear btn")
            // Clear functionality goes here
            newDiv.innerText = ''
            add_item_box.style.display = 'none'
            sum = 0
            total_price.innerText = 0
        };


        clearBtn.addEventListener('click', clear);

    }


    else {
        alert("Please fill in both item name and price.");

    }


});

pay.addEventListener('click', async () => {
    const itemName = item_name.value || 'Default Item';
    const priceValue = sum;

    try {
        const response = await fetch('http://localhost:3000/create-payment-link', {
            method: 'POST',
            headers: {
                'Content-Type': 'application/json',
            },
            body: JSON.stringify({ itemName, price: priceValue }),
        });

        const data = await response.json();
        if (data.url) {
            window.location.href = data.url; // Redirect to the Stripe payment link
        } else {
            alert('Failed to create payment link');
        }
    } catch (error) {
        console.error('Error:', error);
        alert('Error creating payment link');
    }
});
