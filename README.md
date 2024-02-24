# Massticle's Public Repo

Metas available for Asherons's Call

- General (Infinte Leaftide Server)
  - All in one meta for crafting custom leaftide currency, gambling, banking, and attributes.

the inputs for width, height, and title need to reflect in the xml, title should update on change.

```html
<div id="controls" class="container my-3 d-flex">
    <div class="input-group me-2">
        <span class="input-group-text">Width:</span>
        <input type="number" id="canvasWidth" class="form-control" placeholder="Width" min="100" step="10" value="300">
    </div>
    <div class="input-group me-2">
        <span class="input-group-text">Height:</span>
        <input type="number" id="canvasHeight" class="form-control" placeholder="Height" min="100" step="10" value="200">
    </div>
    <div class="input-group me-2">
        <span class="input-group-text">Title:</span>
        <input type="text" id="canvasTitle" class="form-control" placeholder="Test View">
    </div>
    <div class="btn-group me-2">
        <button id="resizeCanvas" class="btn btn-primary">Resize</button>
    </div>
    <div class="btn-group me-2">
        <button id="resetCanvas" class="btn btn-secondary">Reset</button>
    </div>
</div>
```

```js
function generateXml() {
    let xml = '<?xml version="1.0"?>\n';
    xml += '<view width="300" height="200" title="Test View">\n';
    xml += '  <control type="layout">\n';

    $('#squareProperties .square-props').each(function() {
        const index = $(this).data('square-index');
        const square = squares[index];
        let text = $(this).find('.square-text').val().trim() || `Button${index + 1}`;
        const actionexpr = $(this).find('.square-actionexpr').val().trim();
        const setstate = $(this).find('.square-setstate').val().trim();

        xml += `    <control type="button" name="${text}" left="${square.left}" top="${square.top}" width="${square.width}" height="${square.height}" text="${text}"`;

        if(actionexpr) xml += ` actionexpr="${actionexpr}"`;
        if(setstate) xml += ` setstate="${setstate}"`;

        xml += ' />\n';
    });

    xml += '  </control>\n</view>';
    $('#xmlOutput').text(xml);
}


$('#resizeCanvas').click(function () {
    const newWidth = parseInt($('#canvasWidth').val(), 10);
    const newHeight = parseInt($('#canvasHeight').val(), 10);

    if (!isNaN(newWidth) && !isNaN(newHeight) && newWidth > 0 && newHeight > 0) {
        canvas.width = newWidth;
        canvas.height = newHeight;
        redrawSquares();
    } else {
        alert('Please enter valid dimensions');
    }
});

$('#resetCanvas').click(function () {
    squares = []; // Clear the squares array
    ctx.clearRect(0, 0, canvas.width, canvas.height); // Clear the canvas

    // Remove all square property inputs
    $('#squareProperties').empty();

    // Clear the XML output
    $('#xmlOutput').text('');
});
```